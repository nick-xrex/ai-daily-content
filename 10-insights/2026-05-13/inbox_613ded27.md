---
id: inbox_613ded27
date: 2026-05-13
source_ref: "[[00-inbox/.../inbox_613ded27]]"
title: "24+ tok/s from ~30B MoE models on an old GTX 1080 (8 GB VRAM, 128k context)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tcc7h5/24_toks_from_30b_moe_models_on_an_old_gtx_1080_8/
source: reddit-localllama
published_at: 2026-05-13T20:41:56+00:00
fetched_at: 2026-05-19T02:40:36.982968+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶在二手消費級舊硬體（GTX 1080 8GB、i7-6700、32GB RAM，成本 $200）上運行 Qwen 3.6 35B-A3B（~24 tok/s）和 Gemma 4 26B-A4B（~24.5 tok/s 修復版）。關鍵優化為 MoE offloading（將冷門 expert weights 存放系統 RAM，流式傳輸至 GPU）及 --override-tensor-draft 參數調整修復 embedding table PCIe 瓶頸。證明舊卡仍可支援 128k 上下文的大規模 MoE 模型推理。"
key_points:
  - "Qwen 3.6 35B-A3B 在 GTX 1080 達 ~24 tok/s（使用 TurboQuant KV cache 量化，128k 上下文）"
  - "Gemma 4 26B-A4B --override-tensor-draft \"token_embd.weight=CUDA0\" 修復 embedding table 瓶頸，從 ~21 加速至 ~24.5 tok/s 及 79% draft acceptance rate"
  - "MoE offloading 策略：冷門 weights 留在系統 RAM，PCIe 流式傳輸，allow GPU 專注熱層 + KV cache"
tags: [llama-cpp, moe-offloading, gtx-1080, qwen-3.6, gemma-4, optimization]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## 24+ tok/s from ~30B MoE models on an old GTX 1080 (8 GB VRAM, 128k context)

用戶在二手消費級舊硬體（GTX 1080 8GB、i7-6700、32GB RAM，成本 $200）上運行 Qwen 3.6 35B-A3B（~24 tok/s）和 Gemma 4 26B-A4B（~24.5 tok/s 修復版）。關鍵優化為 MoE offloading（將冷門 expert weights 存放系統 RAM，流式傳輸至 GPU）及 --override-tensor-draft 參數調整修復 embedding table PCIe 瓶頸。證明舊卡仍可支援 128k 上下文的大規模 MoE 模型推理。

### 重點
- Qwen 3.6 35B-A3B 在 GTX 1080 達 ~24 tok/s（使用 TurboQuant KV cache 量化，128k 上下文）
- Gemma 4 26B-A4B --override-tensor-draft "token_embd.weight=CUDA0" 修復 embedding table 瓶頸，從 ~21 加速至 ~24.5 tok/s 及 79% draft acceptance rate
- MoE offloading 策略：冷門 weights 留在系統 RAM，PCIe 流式傳輸，allow GPU 專注熱層 + KV cache

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tcc7h5/24_toks_from_30b_moe_models_on_an_old_gtx_1080_8/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# 24+ tok/s from ~30B MoE models on an old GTX 1080 (8 GB VRAM, 128k context)

I got Qwen 3.6 35B-A3B and Gemma 4 26B-A4B running on a $200 secondhand machine (i7-6700 / GTX 1080 / 32 GB RAM) using llama.cpp (the TurboQuant/RotorQuant KV cache quantisation allows 128k context within the 8 GB VRAM). Results (Q4_K_M models, 128k context): Model tok/s Key flags Qwen 3.6 35B-A3B ~24 --n-cpu-moe 30, K=turbo4 V=turbo3 Gemma 4 26B-A4B (no MTP) ~20 --n-cpu-moe 20, K=V=turbo3, --flash-attn Gemma 4 26B-A4B + MTP (naive) ~21 embedding table silently on CPU Gemma 4 26B-A4B + MTP (fixed) ~24.5 --override-tensor-draft &quot;token_embd\.weight=CUDA0&quot; The trick is MoE offloading: llama.cpp can park the cold expert weights in system RAM, and stream over PCIe to the GPU, while keeping hot layers + KV cache on GPU. The system is fully PCIe bandwidth-limited (GPU sits at ~40-50% utilisation while PCIe 3.0 x16 is maxed out). Biggest finding: Gemma 4's MTP speculative decoding barely helps out of the box (~5% gain). Turns out llama.cpp unconditionally keeps the token embedding table on CPU. Normally that's fine (just a get_rows lookup), but Gemma 4's MTP assistant has a tied LM head - so every draft token does a full 262k×1024 matmul across PCIe. Forcing it onto GPU with --override-tensor-draft gives the real ~22% speedup and ~79% draft acceptance rate. Setup pain points (Fedora 42 + Pascal GPU): Pin akmod-nvidia to 580xx branch (Pascal is going legacy) Force gcc-14 for CUDA 12.9 (newer gcc rejected) Patch CUDA's math_functions.h for glibc 2.41 compatibility Used the AtomicBot-ai/atomic-llama-cpp-turboquant fork for both TurboQuant cache + Gemma MTP support Full blog post with all the grindy build details (every command, and the debugging deep-dive into the MTP embedding table issue) I'm also planning a YouTube video walkthrough soon - I'll update when that's live. Happy to answer questions about the setup. &#32; submitted by &#32; /u/mdda [link] &#32; [comments]

</details>