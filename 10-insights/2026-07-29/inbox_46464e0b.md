---
id: inbox_46464e0b
date: 2026-07-29
source_ref: "[[00-inbox/.../inbox_46464e0b]]"
title: "Tokenization: Why LLMs Can&#39;t Count R&#39;s in Strawberry"
url: https://medium.com/@vikrant_bhati/tokenization-why-llms-cant-count-r-s-in-strawberry-059400c33ceb?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-07-29T18:16:44+00:00
fetched_at: 2026-07-31T01:40:09.391797+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者透過『strawberry』計算 R 字數的經典例子，解釋 LLM 無法完成簡單字符計數任務的根本原因。問題不在模型訓練或能力，而在於 tokenization 將文本分解成 token 時，破壞了字符級細節，導致下游任務（如逐字母計數）無法正確執行。文章並質疑 perplexity 指標是否能真實反映模型的實際應用能力，暗示訓練損失與實際表現之間存在重要落差。這個觀察對理解 LLM 的內在局限與適用邊界具有重要參考價值，尤其是在設計涉及字符操作的提示詞時。"
key_points:
  - "Tokenization 過程在 LLM 看到文本前就已分割，導致字符級任務（如逐字母計數、拼寫檢查）的可靠性下降"
  - "『Strawberry』計數 R 字的失敗案例是 tokenization bias 的典型表現，不是模型智能或訓練資料的問題"
  - "Perplexity 等訓練指標未必能預測模型在細粒度文本操縱任務上的實際表現"
tags: [tokenization, llm-limitations, character-counting, token-bias]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Tokenization: Why LLMs Can't Count R's in Strawberry

作者透過『strawberry』計算 R 字數的經典例子，解釋 LLM 無法完成簡單字符計數任務的根本原因。問題不在模型訓練或能力，而在於 tokenization 將文本分解成 token 時，破壞了字符級細節，導致下游任務（如逐字母計數）無法正確執行。文章並質疑 perplexity 指標是否能真實反映模型的實際應用能力，暗示訓練損失與實際表現之間存在重要落差。這個觀察對理解 LLM 的內在局限與適用邊界具有重要參考價值，尤其是在設計涉及字符操作的提示詞時。

### 重點
- Tokenization 過程在 LLM 看到文本前就已分割，導致字符級任務（如逐字母計數、拼寫檢查）的可靠性下降
- 『Strawberry』計數 R 字的失敗案例是 tokenization bias 的典型表現，不是模型智能或訓練資料的問題
- Perplexity 等訓練指標未必能預測模型在細粒度文本操縱任務上的實際表現

**原文：** [medium-tag-llm](https://medium.com/@vikrant_bhati/tokenization-why-llms-cant-count-r-s-in-strawberry-059400c33ceb?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Vikrant Bhati"
published_at: 2026-07-29T18:16:44+00:00
fetched_at: 2026-07-29T23:50:25.981681+00:00
content_hash: "2674798ffeaf5251ac6f8602351c995da4c3591a3694cb1793b6358aa8ced4f9"
lang: en
caption_quality: None
raw: true
topics: []
---

# Tokenization: Why LLMs Can't Count R's in Strawberry

How text becomes tokens before a model ever sees it and why LLM breaks at letter-counting. Does perplexity gives right picture always? Continue reading on Medium »

</details>