---
id: inbox_ecad1664
date: 2026-05-11
source_ref: "[[00-inbox/.../inbox_ecad1664]]"
title: "MTP on Unsloth"
url: https://www.reddit.com/r/LocalLLaMA/comments/1ta4rvs/mtp_on_unsloth/
source: reddit-localllama
published_at: 2026-05-11T14:21:30+00:00
fetched_at: 2026-05-12T01:39:55.178197+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Unsloth 發布了保留 MTP（多令牌預測）層的 Qwen 3.6 模型，包含 27B 和 35B 兩個版本，已上傳至 Hugging Face。使用者可直接下載，但仍需檢查並構建 llamacpp 的 MTP 相關 PR 才能完整啟用該功能。模型卡提供了官方使用說明。"
key_points:
  - "Qwen3.6-27B-GGUF-MTP 和 Qwen3.6-35B-A3B-GGUF-MTP 現已發布"
  - "需要額外構建 llamacpp MTP PR 以完整支援"
  - "模型卡內含詳細配置指南"
tags: [unsloth, qwen3.6, mtp, gguf, local-llm]
topics: []
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## MTP on Unsloth

Unsloth 發布了保留 MTP（多令牌預測）層的 Qwen 3.6 模型，包含 27B 和 35B 兩個版本，已上傳至 Hugging Face。使用者可直接下載，但仍需檢查並構建 llamacpp 的 MTP 相關 PR 才能完整啟用該功能。模型卡提供了官方使用說明。

### 重點
- Qwen3.6-27B-GGUF-MTP 和 Qwen3.6-35B-A3B-GGUF-MTP 現已發布
- 需要額外構建 llamacpp MTP PR 以完整支援
- 模型卡內含詳細配置指南

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1ta4rvs/mtp_on_unsloth/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# MTP on Unsloth

https://huggingface.co/unsloth/Qwen3.6-27B-GGUF-MTP https://huggingface.co/unsloth/Qwen3.6-35B-A3B-GGUF-MTP Unsloth release the model with preserved MTP layer, but you still have to checkout and build llamacpp pr about MTP. just open HF link, Unsloth give the instruction how to use MTP in the model card &#32; submitted by &#32; /u/Altruistic_Heat_9531 [link] &#32; [comments]

</details>