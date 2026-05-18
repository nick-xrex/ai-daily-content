---
id: inbox_39949f4a
date: 2026-05-17
source_ref: "[[00-inbox/.../inbox_39949f4a]]"
title: "Dual GPU llama.cpp speedup"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tflngz/dual_gpu_llamacpp_speedup/
source: reddit-localllama
published_at: 2026-05-17T10:24:36+00:00
fetched_at: 2026-05-18T04:09:16.232140+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RedToasty 分享改進的 llama.cpp tensor split fork，修復 `--split-mode tensor` 在量化 KV cache 下的支援限制。使用 Q8_0 量化 KV cache，在雙 GPU (3060 12GB + 4070 Super 12GB) 環境下，tg32 生成模式速度提升 41.7%（30.05 vs 21.22 tokens/s）。實測個人使用從 25 tps 提升至 40 tps（短上下文），新 fork 同時支援最新 MTP speculative decoding (`--spec-type draft-mtp`)，但對 MoE 模型仍有相容性問題。"
key_points:
  - "Tensor split 配合 Q8_0 量化 KV cache，tg32 模式 41.7% 速度提升（30.05 vs 21.22 t/s）"
  - "實測應用：短上下文從 25 tps → 40 tps，利用 speculative decoding 最佳配置 `--spec-draft-p-min 0.75 --spec-draft-n-max 2`"
  - "支援 Qwen 3.6 27B/9B 等 dense 模型，MoE 相容性待解決"
tags: [llama.cpp, multi-gpu, tensor-split, kv-cache-quantization, speculative-decoding]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Dual GPU llama.cpp speedup

RedToasty 分享改進的 llama.cpp tensor split fork，修復 `--split-mode tensor` 在量化 KV cache 下的支援限制。使用 Q8_0 量化 KV cache，在雙 GPU (3060 12GB + 4070 Super 12GB) 環境下，tg32 生成模式速度提升 41.7%（30.05 vs 21.22 tokens/s）。實測個人使用從 25 tps 提升至 40 tps（短上下文），新 fork 同時支援最新 MTP speculative decoding (`--spec-type draft-mtp`)，但對 MoE 模型仍有相容性問題。

### 重點
- Tensor split 配合 Q8_0 量化 KV cache，tg32 模式 41.7% 速度提升（30.05 vs 21.22 t/s）
- 實測應用：短上下文從 25 tps → 40 tps，利用 speculative decoding 最佳配置 `--spec-draft-p-min 0.75 --spec-draft-n-max 2`
- 支援 Qwen 3.6 27B/9B 等 dense 模型，MoE 相容性待解決

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tflngz/dual_gpu_llamacpp_speedup/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Dual GPU llama.cpp speedup

Llama.cpp has an issue with &quot;--split-mode tensor&quot;, you'll get great results but it only supports non-quantized KV caches, for this very reason a lot of people decide to go with a healthy sized KV cache and ignore tensor parallelism. &nbsp; I've had a stab at fixing the issue here - https://github.com/RedToasty/llama.cpp_qts - it's branched from mainline as of today, with minimal changes. &nbsp; I'm personally running a 3060 12gb + 4070 Super 12gb, for a combined 24gb. &nbsp; Here's my results with Q8_0/Q8_0 and &quot;-sm tensor&quot;: &nbsp; llama-bench.exe -m Qwen3.6-27B-Q4_K_M.gguf -sm tensor -fa 1 -ctk q8_0 -ctv q8_0 -p 128 -n 32 -b 128 -ub 128 &nbsp; Model Size Params Backend NGL Batch UBatch Type K Type V SM FA Test Tokens/s Qwen3.5 27B Q4_K Medium 15.65 GiB 26.90 B CUDA 99 128 128 q8_0 q8_0 tensor 1 pp128 544.82 ± 6.01 Qwen3.5 27B Q4_K Medium 15.65 GiB 26.90 B CUDA 99 128 128 q8_0 q8_0 tensor 1 tg32 30.05 ± 0.38 Here's without tensor splitting: &nbsp; llama-bench.exe -m Qwen3.6-27B-Q4_K_M.gguf -fa 1 -ctk q8_0 -ctv q8_0 -p 128 -n 32 -b 128 -ub 128 &nbsp; Model Size Params Backend NGL Batch UBatch Type K Type V FA Test Tokens/s Qwen3.5 27B Q4_K Medium 15.65 GiB 26.90 B CUDA 99 128 128 q8_0 q8_0 1 pp128 582.60 ± 28.57 Qwen3.5 27B Q4_K Medium 15.65 GiB 26.90 B CUDA 99 128 128 q8_0 q8_0 1 tg32 21.22 ± 0.52 Just over a 40% speed increase, with no loss of quality . This branch also supports the latest mtp changes , I've personally been using: &nbsp; --spec-type draft-mtp --spec-draft-p-min 0.75 --spec-draft-n-max 2 &nbsp; In personal use my tokens per second have gone from around 25tps to around 40tps, in short &quot;write a story&quot; style contexts. I think it's due to limited vram, but I've personally had more joy with ngram-mod when using agentic coding and longer contexts. &nbsp; I'd love to hear any feedback from anyone running dual 5060 ti or similar. Also anything dual Vulkan would be interesting, I'm looking for issues. &nbsp; TLDR : If you run dual GPUs, grab/build this fork, add &quot;-sm tensor&quot; to your current command line and see if it goes 50% faster! Note : I've just spotted there's an issue with MoE models and &quot;-sm tensor&quot;, not related to this fix. Test against dense models for the moment, Qwen3.6 27b/9b etc. Tensor split seems very unloved, given it's a free 50% boost! If this proves popular I'll look at fixing MoE and pulling Turboquants in. &#32; submitted by &#32; /u/Legitimate-Dog5690 [link] &#32; [comments]

</details>