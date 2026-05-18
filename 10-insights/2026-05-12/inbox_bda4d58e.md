---
id: inbox_bda4d58e
date: 2026-05-12
source_ref: "[[00-inbox/2026-05-12/1800-reddit-localllama-qwen3-6-27b-q5-k-m-mtp-256k-context-5090-6c3e]]"
title: "Qwen3.6 27b q5_k_M MTP - 256k context - 5090"
url: https://www.reddit.com/r/LocalLLaMA/comments/1taz3eu/qwen36_27b_q5_k_m_mtp_256k_context_5090/
source: reddit-localllama
published_at: 2026-05-12T11:43:51+00:00
fetched_at: 2026-05-12T18:12:25.044057+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "在 RTX 5090 上成功運行 Qwen3.6-27B Q5_K_M 搭配 MTP speculative decoding，達成 256k context 且無 memory spillover。使用 llama.cpp 特殊版本（PR #22673），配置 MTP 最大 draft tokens 為 3，cache 量化為 q8_0，速度 65-75 tok/s。核心是需要專門支持 MTP 的 llama.cpp 版本。"
key_points:
  - "Qwen3.6 27B Q5_K_M 搭 MTP 和 q8_0 cache 量化在 RTX 5090 上可運行 256k context"
  - "需要 llama.cpp PR #22673 特殊版本才能支持 Qwen3.6 + MTP 組合"
  - "推理速度 65-75 tok/s，適合本地部署"
tags: [qwen3.6, mtp, context-window, llama-cpp, quantization]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen3.6 27b q5_k_M MTP - 256k context - 5090

在 RTX 5090 上成功運行 Qwen3.6-27B Q5_K_M 搭配 MTP speculative decoding，達成 256k context 且無 memory spillover。使用 llama.cpp 特殊版本（PR #22673），配置 MTP 最大 draft tokens 為 3，cache 量化為 q8_0，速度 65-75 tok/s。核心是需要專門支持 MTP 的 llama.cpp 版本。

### 重點
- Qwen3.6 27B Q5_K_M 搭 MTP 和 q8_0 cache 量化在 RTX 5090 上可運行 256k context
- 需要 llama.cpp PR #22673 特殊版本才能支持 Qwen3.6 + MTP 組合
- 推理速度 65-75 tok/s，適合本地部署

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1taz3eu/qwen36_27b_q5_k_m_mtp_256k_context_5090/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

￼Straight to it: llama-server-mtp \ -m ~/models/Qwen3.6-27B-Q5_K_M-mtp.gguf \ --spec-type mtp \ --spec-draft-n-max 3 \ --cache-type-k q8_0 \ --cache-type-v q8_0 \ -np 1 \ -c 262144 \ -ngl 99 \ --host 0.0.0.0 \ --port 8080 Been running this on my desktop 5090 with no issues and no spillover! You will need to install a special version of llamacpp to run Qwen3.6 with MTP: https://github.com/ggml-org/llama.cpp/pull/22673 Edit: 65-75 tps &#32; submitted by &#32; /u/No_Mango7658 [link] &#32; [comments]

</details>