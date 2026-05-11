---
id: inbox_5d853de4
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_5d853de4]]"
title: "DeepSeek-V4-Flash W4A16+FP8 with MTP self-speculation: 85 tok/s @ 524k on 2× RTX PRO 6000 Max-Q"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t9em98/deepseekv4flash_w4a16fp8_with_mtp_selfspeculation/
source: reddit-localllama
published_at: 2026-05-10T18:22:24+00:00
fetched_at: 2026-05-11T02:22:04.453731+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者 LordNeel 發布了優化版 DeepSeek-V4-Flash-Acti-MTP-W4A16-FP8 模型，在 2× RTX PRO 6000 Max-Q（共 192GB 顯存）上透過 Multi-Token Prediction (MTP) 自投機技術實現推理速度大幅提升。在 524k token 上下文中，解碼速度從原始的 52.85 tok/s 提升至 85.52 tok/s（+62%），於 128k 上下文時達 ~111 tok/s（+110%）。模型包含 671B 總參數、32B 活躍參數，使用 W4A16 INT4 group=128 對稱量化搭配 GPTQ 優化，涵蓋 768 個路由專家的量化。開發者另提供詳細 AGENTS.md 運行手冊，包含 NCCL 調優參數與 Max-Q 特定修正（--disable-custom-all-reduce）以解決 PCIe 拓撲死鎖問題。"
key_points:
  - "DeepSeek-V4-Flash W4A16+FP8 量化版在 2× RTX PRO 6000 Max-Q 上，藉 MTP 自投機於 524k context 達 85.52 tok/s（相比無 MTP 的 52.85 tok/s 提升 62%），128k context 達 ~111 tok/s（提升 110%）"
  - "768 個路由專家採用 W4A16 INT4 group=128 對稱量化 + GPTQ 優化，利用 17,701 MTP 前向 dump 與 473k tokens 校準"
  - "針對 Max-Q PCIe-only 拓撲提供硬體修正：--disable-custom-all-reduce 避免共享記憶體死鎖；NCCL 調優（LL/Ring/min-ch=8/nthreads=512）將 TTFT 從 155ms 降至 91ms"
tags: [deepseek-v4, quantization-w4a16, mtp-speculation, vllm-optimization, rtx-pro-6000]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## DeepSeek-V4-Flash W4A16+FP8 with MTP self-speculation: 85 tok/s @ 524k on 2× RTX PRO 6000 Max-Q

開發者 LordNeel 發布了優化版 DeepSeek-V4-Flash-Acti-MTP-W4A16-FP8 模型，在 2× RTX PRO 6000 Max-Q（共 192GB 顯存）上透過 Multi-Token Prediction (MTP) 自投機技術實現推理速度大幅提升。在 524k token 上下文中，解碼速度從原始的 52.85 tok/s 提升至 85.52 tok/s（+62%），於 128k 上下文時達 ~111 tok/s（+110%）。模型包含 671B 總參數、32B 活躍參數，使用 W4A16 INT4 group=128 對稱量化搭配 GPTQ 優化，涵蓋 768 個路由專家的量化。開發者另提供詳細 AGENTS.md 運行手冊，包含 NCCL 調優參數與 Max-Q 特定修正（--disable-custom-all-reduce）以解決 PCIe 拓撲死鎖問題。

### 重點
- DeepSeek-V4-Flash W4A16+FP8 量化版在 2× RTX PRO 6000 Max-Q 上，藉 MTP 自投機於 524k context 達 85.52 tok/s（相比無 MTP 的 52.85 tok/s 提升 62%），128k context 達 ~111 tok/s（提升 110%）
- 768 個路由專家採用 W4A16 INT4 group=128 對稱量化 + GPTQ 優化，利用 17,701 MTP 前向 dump 與 473k tokens 校準
- 針對 Max-Q PCIe-only 拓撲提供硬體修正：--disable-custom-all-reduce 避免共享記憶體死鎖；NCCL 調優（LL/Ring/min-ch=8/nthreads=512）將 TTFT 從 155ms 降至 91ms

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t9em98/deepseekv4flash_w4a16fp8_with_mtp_selfspeculation/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# DeepSeek-V4-Flash W4A16+FP8 with MTP self-speculation: 85 tok/s @ 524k on 2× RTX PRO 6000 Max-Q

TL;DR : DeepSeek-V4-Flash running at 85.52 tok/s @ 524k ctx and ~111 tok/s @ 128k single-stream on 2× RTX PRO 6000 Max-Q pasta-paul's DeepSeek-V4-Flash-W4A16-FP8 quant is great, but its MTP head silently gets stripped at load time (HF transformers has it in _keys_to_ignore_on_load_unexpected ), so --speculative-config '{&quot;method&quot;:&quot;mtp&quot;,...}' is a no-op. Retrofitted the MTP block, ran a GPTQ pass on its routed experts to match the base's W4A16 INT4 group format, and patched vLLM. Decode goes from 52.85 tok/s (no MTP) → 85.52 tok/s @ 524k 2-stream → ~111 tok/s @ 128k single-stream . 671B total / 32B active, fits on 2× 96 GB. Model: https://huggingface.co/LordNeel/DeepSeek-V4-Flash-Acti-MTP-W4A16-FP8 Numbers 2× RTX PRO 6000 Blackwell Max-Q (96 GB each, no NVLink, sm_120): Profile Decode TPS TTFT Δ vs base pasta-paul base, no MTP, 524k 52.85 91 ms reference This model, 524k 2-stream 85.52 155 ms +62% (1.62×) This model, 128k single-stream ~111 ~310 ms +110% (2.10×) Sanity-check benchmarks (small samples, full data in the model card): Benchmark n Score GSM8K (T=0, COT, exact-match) 100 93% MMLU (mixed subjects) 100 53% (sample dragged by hard subjects; tracks base) HumanEval (syntactic check, not pass@1 exec) 50 90% What got quantized how 768 routed-expert tensors (256 experts × {w1, w2, w3}): W4A16 INT4 group=128 sym, GPTQ (Frantar-style with Cholesky H−1). Calibrated with 256 ultrachat_200k prompts × 256 max_tokens captured from the running pasta-paul model — 17,701 MTP forward dumps, 473k tokens. 5 attention projections : FP8_BLOCK (kept upstream's FP8 weights, just renamed scale → weight_scale to match pasta-paul's compressed-tensors convention). Shared experts, e_proj, h_proj, norms, gate, attn_sink : BF16 / FP32. Max-Q specific fixes: If you're on the Max-Q workstation cards specifically : you MUST pass --disable-custom-all-reduce . vLLM's CustomAllreduce uses CUDA P2P (independent of NCCL_P2P_DISABLE ), and on PCIe-only Max-Q topology it deadlocks at post-graph eager warmup. Without the flag the engine hangs at gpu_worker.py:619 with infinite shm_broadcast.py:681 No available shared memory broadcast block warnings. The Server variant has NVLink and does not hit this. NCCL tuning that drops TTFT from ~155 ms to ~91 ms on Max-Q at zero decode-TPS cost: NCCL_PROTO=LL NCCL_ALGO=Ring NCCL_MIN_NCHANNELS=8 NCCL_NTHREADS=512 How to run Needs the patched vLLM fork. Vanilla doesn't load DSV4-Flash quants. Base workspace at https://github.com/pasta-paul/dsv4-flash-w4a16-fp8 . Apply the MTP patches on top. vllm serve LordNeel/DeepSeek-V4-Flash-Acti-MTP-W4A16-FP8 \ --tensor-parallel-size 2 --kv-cache-dtype fp8 --block-size 256 \ --max-model-len 524288 --max-num-seqs 2 \ --gpu-memory-utilization 0.93 \ --tokenizer-mode deepseek_v4 \ --tool-call-parser deepseek_v4 --enable-auto-tool-choice \ --reasoning-parser deepseek_v4 \ --trust-remote-code \ --disable-custom-all-reduce \ --speculative-config '{&quot;method&quot;:&quot;mtp&quot;,&quot;num_speculative_tokens&quot;:1}' \ --host 0.0.0.0 --port 8000 I also wrote an AGENTS.md runbook. Point Claude/Codex/Cursor to it and tell it &quot;set this up&quot;/ &quot;verify hardware and get this model running&quot;/ or similar. Goes through preflight → CUDA toolkit (no sudo via conda) → patched vLLM build → download → patches → serve → smoke test. Limitations TP=2 only. TP=1 OOMs on a single RTX6000 pro; TP≥4 hits an upstream W4A16 MoE scale-sharding bug ( vllm-project/vllm#41511 ). num_speculative_tokens capped at 1. DSV4 flash ships exactly one MTP head ( num_nextn_predict_layers=1 ); higher values will not produce more drafts. Reasoning parser caveat. With --reasoning-parser deepseek_v4 , output splits into content and reasoning_content . Clients reading only content see empty strings on &quot;thinking&quot; responses. MTP GPTQ skipped attention during calibration — see Future work in card. Hardware tested: only Max-Q. Server variant + DGX Spark + H200 should work but I have not run them. Request for the community If you run this and the MTP draft acceptance rate comes out significantly different on your prompt distribution, please do comment with your domain and the rate (vLLM will log it as spec_decode_acceptance_rate ). Credits DeepSeek-AI for the base model pasta-paul for the W4A16+FP8 quant + jasl/vllm serving stack ( repo ) &#32; submitted by &#32; /u/Blahblahblakha [link] &#32; [comments]

</details>