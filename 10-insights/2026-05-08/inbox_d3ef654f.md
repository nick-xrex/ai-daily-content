---
id: inbox_d3ef654f
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0151-reddit-localllama-got-mtp-turboquant-running-qwen3-6-27b-8-a08c]]"
title: "Got MTP + TurboQuant running — Qwen3.6-27B -- 80+ t/s at 262K context on a single RTX 4090"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t7kyju/got_mtp_turboquant_running_qwen3627b_80_ts_at/
source: reddit-localllama
published_at: 2026-05-08T21:15:59+00:00
fetched_at: 2026-05-09T02:10:25.345782+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶在 RTX 4090 上成功運行 MTP + TurboQuant 優化的 Qwen3.6-27B，達到 80–87 tokens/秒（從初始 43 t/s 提升），262K 上下文窗口配合 TBQ4_0 無損 KV 緩存量化。MTP draft 接受率為 73%。採用 Q4_K_M 量化模型，測試環境為 Ubuntu 24.04 + CUDA 12.x。此優化方案已開源，可用於本地推理場景。"
key_points:
  - "Token 吞吐量 80–87 t/s（較優化前 43 t/s 增長 87–102%）"
  - "262K 上下文 + TBQ4_0（4.25 bpv）KV 緩存量化 + MTP draft 73% 接受率"
  - "RTX 4090 24GB 單卡支撐，代碼已開源於 llama.cpp-mtp 分支"
tags: [qwen, mtp, turboquant, kv-cache-quantization, local-inference]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Got MTP + TurboQuant running — Qwen3.6-27B -- 80+ t/s at 262K context on a single RTX 4090

用戶在 RTX 4090 上成功運行 MTP + TurboQuant 優化的 Qwen3.6-27B，達到 80–87 tokens/秒（從初始 43 t/s 提升），262K 上下文窗口配合 TBQ4_0 無損 KV 緩存量化。MTP draft 接受率為 73%。採用 Q4_K_M 量化模型，測試環境為 Ubuntu 24.04 + CUDA 12.x。此優化方案已開源，可用於本地推理場景。

### 重點
- Token 吞吐量 80–87 t/s（較優化前 43 t/s 增長 87–102%）
- 262K 上下文 + TBQ4_0（4.25 bpv）KV 緩存量化 + MTP draft 73% 接受率
- RTX 4090 24GB 單卡支撐，代碼已開源於 llama.cpp-mtp 分支

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t7kyju/got_mtp_turboquant_running_qwen3627b_80_ts_at/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

So I've been messing around trying to get MTP working alongside TBQ4_0 (TurboQuant's lossless 4.25 bpv KV cache) on Qwen3.6-27B for my own use. So after a day of vibecoding I think I may have gotten something viable. Went from about 43 t/s when I first got it compiling to 80-87 t/s after optimizing. With MTP draft acceptance around 73% on top of that. Running on: - RTX 4090 24GB - Qwen3.6-27B-Heretic-v2 Q4_K_M with grafted MTP heads - 262K context, TBQ4_0 KV cache, MTP draft 3 - Ubuntu 24.04, CUDA 12.x I'm not a professional or anything so there's probably room for improvement, but it works and the output quality seems solid. The fork's buildable if anyone wants to try it or poke holes in the approach: https://github.com/Indras-Mirror/llama.cpp-mtp Got Deepseek to write up the technical details here if anyone's curious about the kernel architecture: https://indrasmirror.au/blog-mtp-shared-tensors-200k.html &#32; submitted by &#32; /u/indrasmirror [link] &#32; [comments]

</details>