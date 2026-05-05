---
id: inbox_fba99f02
date: 2026-05-05
source_ref: "[[00-inbox/2026-05-05/0819-reddit-localllama-qwen3-6-27b-fp8-runs-with-200k-tokens-of-a834]]"
title: "Qwen3.6 27B FP8 runs with 200k tokens of BF16 KV cache at 80 TPS on a single RTX 5000 PRO 48GB"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t46klu/qwen36_27b_fp8_runs_with_200k_tokens_of_bf16_kv/
source: reddit-localllama
published_at: 2026-05-05T05:46:22+00:00
fetched_at: 2026-05-05T08:38:51.523671+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶分享在 RTX 5000 PRO 48GB 上運行 Qwen3.6-27B-FP8 的優化配置方案。核心策略：使用官方 FP8 量化模型搭配 BF16（非量化）KV 緩存，避免量化誤差複合放大，同時利用 Blackwell 硬體加速。支援 200k token 長上下文、60-90 TPS 編碼性能（MTP=2），無需早期壓縮。vLLM 0.20.1 配置包含 FLASHINFER 後端、MTP=2 推測解碼、cudagraph FULL_AND_PIECEWISE、GPU 記憶體利用率 97.5% 等多項優化。"
key_points:
  - "FP8 量化模型 + BF16 KV 組合策略：最小化量化誤差複合，適合長上下文代理編碼任務"
  - "Qwen3.6-27B-FP8 on RTX 5000 PRO 48GB 達成：200k token @ 1.09x 並發、60-90 TPS（MTP=2 推測）"
  - "vLLM 0.20.1 多項配置優化：FLASHINFER 後端 + MTP 推測 + cudagraph FULL_AND_PIECEWISE 編譯 + 97.5% GPU 利用率"
tags: [qwen3.6-fp8, vllm-0.20.1, 200k-tokens, rtx-5000-pro, mtp-speculative]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen3.6 27B FP8 runs with 200k tokens of BF16 KV cache at 80 TPS on a single RTX 5000 PRO 48GB

用戶分享在 RTX 5000 PRO 48GB 上運行 Qwen3.6-27B-FP8 的優化配置方案。核心策略：使用官方 FP8 量化模型搭配 BF16（非量化）KV 緩存，避免量化誤差複合放大，同時利用 Blackwell 硬體加速。支援 200k token 長上下文、60-90 TPS 編碼性能（MTP=2），無需早期壓縮。vLLM 0.20.1 配置包含 FLASHINFER 後端、MTP=2 推測解碼、cudagraph FULL_AND_PIECEWISE、GPU 記憶體利用率 97.5% 等多項優化。

### 重點
- FP8 量化模型 + BF16 KV 組合策略：最小化量化誤差複合，適合長上下文代理編碼任務
- Qwen3.6-27B-FP8 on RTX 5000 PRO 48GB 達成：200k token @ 1.09x 並發、60-90 TPS（MTP=2 推測）
- vLLM 0.20.1 多項配置優化：FLASHINFER 後端 + MTP 推測 + cudagraph FULL_AND_PIECEWISE 編譯 + 97.5% GPU 利用率

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t46klu/qwen36_27b_fp8_runs_with_200k_tokens_of_bf16_kv/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>----START HUMAN TEXT----</p> <p>Hi all,</p> <p>I've seen a bunch of posts about squeezing 27B onto a 24GB card and all the quantization tricks involved in doing so. It's all amazing work, but at the end of the day a quantized model with quantized KV will inevitably compound errors faster than non-quantized ones, which noticeably impacts agentic coding.</p> <p>I figured a 48GB GPU offered just enough VRAM to avoid most of the quantization nastiness with genuinely good options, like Blackwell-accelerated FP8. Luckily, Qwen released their own FP8 variant of the 27B model.</p> <p>I'm serious when I say: I think we might have an answer to all those &quot;what do I buy for $10k?&quot; posts. A pro5k, 64GB RAM, a decent CPU/mobo, and it will run the FP8 quant of 27B with Blackwell hardware acceleration and non-quantized KV like a champ. It's quiet, cool enough, small, fast... really great.</p> <p>The end recipe:</p> <ul> <li>vLLM 0.20.1</li> <li>CUDA 12.9</li> <li><a href="https://huggingface.co/Qwen/Qwen3.6-27B-FP8">Qwen's official FP8 quant of Qwen3.6 27B</a> which gives all the features of Qwen3.6 like multi-modality, MTP, etc.</li> <li>BF16 KV cache with 200k tokens @ 1.09x concurrency</li> <li>Real benchmark numbers to follow - they're running now.</li> </ul> <p>These settings:</p> <pre><code>export VLLM_USE_FLASHINFER_MOE_FP8=1 export VLLM_TEST_FORCE_FP8_MARLIN=1 export VLLM_SLEEP_WHEN_IDLE=1 export VLLM_MEMORY_PROFILER_ESTIMATE_CUDAGRAPHS=1 export VLLM_LOG_STATS_INTERVAL=2 export VLLM_WORKER_MULTIPROC_METHOD=spawn export SAFETENSORS_FAST_GPU=1 export CUDA_DEVICE_ORDER=PCI_BUS_ID export TORCH_FLOAT32_MATMUL_PRECISION=high export PYTORCH_ALLOC_CONF=expandable_segments:True vllm serve Qwen/Qwen3.6-27B-FP8 \ --host 0.0.0.0 --port 8080 \ --performance-mode interactivity \ --trust-remote-code \ --enable-auto-tool-choice \ --tool-call-parser qwen3_coder \ --reasoning-parser qwen3 \ --mm-encoder-tp-mode data \ --mm-processor-cache-type shm \ --gpu-memory-utilization 0.975 \ --speculative-config '{&quot;method&quot;:&quot;mtp&quot;,&quot;num_speculative_tokens&quot;:2}' \ --compilation-config '{&quot;cudagraph_mode&quot;: &quot;FULL_AND_PIECEWISE&quot;, &quot;max_cudagraph_capture_size&quot;: 16, &quot;mode&quot;: &quot;VLLM_COMPILE&quot;}' \ --async-scheduling \ --attention-backend flashinfer \ --max-model-len 196608 \ --kv-cache-dtype bfloat16 \ --enable-prefix-caching </code></pre> <p><strong>Performance</strong></p> <p>I'm running real benchmarks right now and will update this post later, but in general: writing code with MTP=2 yields 60-90 TPS, which is a number I find perfectly acceptable for daily use. Furthermore, because we're running the FP8 and KV is non-quantized we get the benefits of long Claude sessions without early compaction, endless loops, etc. It's truly minimally quantized.</p> <p>----END HUMAN TEXT----</p> <p><strong>If there were AI-generated text it would follow here.</strong></p> <p>----START AI TEXT----</p> <p>----END AI TEXT----</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/__JockY__"> /u/__JockY__ </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t46klu/qwen36_27b_fp8_runs_with_200k_tokens_of_bf16_kv/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t46klu/qwen36_27b_fp8_runs_with_200k_tokens_of_bf16_kv/">[comments]</a></span>

</details>