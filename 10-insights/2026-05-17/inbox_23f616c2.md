---
id: inbox_23f616c2
date: 2026-05-17
source_ref: "[[00-inbox/.../inbox_23f616c2]]"
title: "Testing llama.cpp MTP support on Qwen3.6 - RTX 5090"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tfgxc8/testing_llamacpp_mtp_support_on_qwen36_rtx_5090/
source: reddit-localllama
published_at: 2026-05-17T06:00:43+00:00
fetched_at: 2026-05-18T04:08:06.627414+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reddit 使用者在 RTX 5090 上測試 llama.cpp 的 MTP (Multi-Token Prediction) 特性對 Qwen3.6 的推理速度影響。硬體：RTX 5090 32GB、自編譯 llama.cpp (commit 4f13cb7，含 CUDA support)、Qwen3.6-27B-MTP-GGUF Q5_K_M 及 35B-A3B Q4 版本。測試設定：128k context、flash-attention、q8_0 KV cache、溫度 0.8、--parallel 1（MTP 要求）、MTP on/off 對照（--spec-type draft-mtp --spec-draft-n-max 3）。測試用例：短故事（~400 token）與 Flappy Bird HTML（~3000 token），各 3 次種子取平均。文章未展示具體速度結果，但設置詳細、隔離變量嚴謹，適合重現實驗。"
key_points:
  - "llama.cpp MTP 支持需從 source 編譯（CUDA_DOCKER_ARCH=120），官方鏡像尚未更新"
  - "MTP 推理需禁用並行（--parallel 1）與使用特定 flag：--spec-type draft-mtp --spec-draft-n-max 3"
  - "實驗隔離變量完全（同一 GGUF、僅改 MTP 開關），適合評估 MTP 純淨效果"
tags: [llama.cpp, mtp, qwen3.6, rtx-5090, inference-optimization]
topics: []
importance: 3
novelty: 4
insight_quality: 2
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Testing llama.cpp MTP support on Qwen3.6 - RTX 5090

Reddit 使用者在 RTX 5090 上測試 llama.cpp 的 MTP (Multi-Token Prediction) 特性對 Qwen3.6 的推理速度影響。硬體：RTX 5090 32GB、自編譯 llama.cpp (commit 4f13cb7，含 CUDA support)、Qwen3.6-27B-MTP-GGUF Q5_K_M 及 35B-A3B Q4 版本。測試設定：128k context、flash-attention、q8_0 KV cache、溫度 0.8、--parallel 1（MTP 要求）、MTP on/off 對照（--spec-type draft-mtp --spec-draft-n-max 3）。測試用例：短故事（~400 token）與 Flappy Bird HTML（~3000 token），各 3 次種子取平均。文章未展示具體速度結果，但設置詳細、隔離變量嚴謹，適合重現實驗。

### 重點
- llama.cpp MTP 支持需從 source 編譯（CUDA_DOCKER_ARCH=120），官方鏡像尚未更新
- MTP 推理需禁用並行（--parallel 1）與使用特定 flag：--spec-type draft-mtp --spec-draft-n-max 3
- 實驗隔離變量完全（同一 GGUF、僅改 MTP 開關），適合評估 MTP 純淨效果

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tfgxc8/testing_llamacpp_mtp_support_on_qwen36_rtx_5090/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Testing llama.cpp MTP support on Qwen3.6 - RTX 5090

Setup: - RTX 5090, 32 GB, Linux - Built llama.cpp from 4f13cb7 (the official ghcr.io/ggml-org/llama.cpp:server-cuda image hasn't picked up the merge yet as of writing — had to docker build from source with CUDA_DOCKER_ARCH=120) - Unsloth's Qwen3.6-27B-MTP-GGUF Q5_K_M and Qwen3.6-35B-A3B-MTP-GGUF UD-Q4_K_M - 128k context, flash-attn, q8_0 KV cache, temp 0.8, --parallel 1 (required for MTP) - Same GGUF for &quot;MTP on&quot; and &quot;MTP off&quot; — only the --spec-type draft-mtp --spec-draft-n-max 3 flag toggled. This isolates MTP from quant differences. - 2 prompts: &quot;short story about a cat&quot; (~400 tokens) and &quot;Flappy Bird clone as a single HTML file&quot; (~3000 tokens) - 3 seeds per config, averaged &#32; submitted by &#32; /u/3VITAERC [link] &#32; [comments]

</details>