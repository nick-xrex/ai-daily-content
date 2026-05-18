---
id: inbox_60f6fa61
date: 2026-05-12
source_ref: "[[00-inbox/2026-05-12/1800-reddit-localllama-how-do-i-use-mtp-3c7f]]"
title: "How do I use MTP?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tazv4k/how_do_i_use_mtp/
source: reddit-localllama
published_at: 2026-05-12T12:16:59+00:00
fetched_at: 2026-05-12T18:14:18.622387+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "社群成員詢問 llama.cpp MTP 使用方式，在執行 Qwen3.6-27B-GGUF-MTP 時遇到「--spec-type 參數未知」編譯錯誤。經社群協助，發現根本原因是編譯指令不正確，修正後問題解決。反映 MTP 工具鏈的初期使用門檻。"
key_points:
  - "MTP 模型使用需搭配正確的 llama.cpp 編譯配置"
  - "常見錯誤：未用正確的 MTP 分支編譯導致 --spec-type 參數無法識別"
  - "Qwen3.6-27B-GGUF-MTP 是支援該技術的模型變體"
tags: [llama.cpp, mtp, compilation, troubleshooting]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## How do I use MTP?

社群成員詢問 llama.cpp MTP 使用方式，在執行 Qwen3.6-27B-GGUF-MTP 時遇到「--spec-type 參數未知」編譯錯誤。經社群協助，發現根本原因是編譯指令不正確，修正後問題解決。反映 MTP 工具鏈的初期使用門檻。

### 重點
- MTP 模型使用需搭配正確的 llama.cpp 編譯配置
- 常見錯誤：未用正確的 MTP 分支編譯導致 --spec-type 參數無法識別
- Qwen3.6-27B-GGUF-MTP 是支援該技術的模型變體

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tazv4k/how_do_i_use_mtp/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hi, I'm trying to use MTP with llama.cpp, I built from source the mtp-pr, download an MTP model from huggingface https://huggingface.co/unsloth/Qwen3.6-27B-GGUF-MTP/resolve/main/Qwen3.6-27B-Q6_K.gguf But when I run the model I have an error: error while handling argument &quot;--spec-type&quot;: unknown speculative decoding type without draft model Can someone tell me what I'm doing wrong? SOLVED: I used the wrong build command, thanks for you help :) &#32; submitted by &#32; /u/WhatererBlah555 [link] &#32; [comments]

</details>