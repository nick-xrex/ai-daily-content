---
id: inbox_12df9c0d
date: 2026-05-24
source_ref: "[[00-inbox/2026-05-24/0011-medium-tag-llm-what-are-tokens-in-llms-how-large-langua-fe93]]"
title: "What Are Tokens in LLMs? How Large Language Models Read, Count, and Process Text"
url: https://medium.com/@amoljp19/what-are-tokens-in-llms-how-large-language-models-read-count-and-process-text-1a69a01b294a?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-24T15:01:12+00:00
fetched_at: 2026-05-25T00:21:09.637202+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章解釋 LLM 中「令牌」(Token) 的基本概念及其實踐影響。令牌是文本的最小處理單位，不是完整詞彙，而是單字、詞碎片、標點、數字或空白；ChatGPT 及其他 AI 工具會將輸入分解為令牌序列處理。令牌計數與限制直接影響用戶體驗：「超過上下文視窗」「輸入過長」等錯誤源於令牌數量；模型容量規格（如 128K 令牌）定義可用上下文長度；費用按令牌計費，影響成本預算。理解令牌概念是現代 AI 素養基礎，有助用戶理解模型容量、價格與互動限制的來源。"
key_points:
  - "令牌定義：子詞單位（單字、詞碎片、標點、數字、空白或程式碼符號），非完整詞彙"
  - "上下文視窗與價格：令牌計數決定可用上下文長度與計費額度，限制模型輸入容量"
  - "AI 素養：掌握令牌概念後，上下文限制、模型規格（128K tokens）、分層價格等行為變可理解"
tags: [tokens, llms, tokenization, context-window, pricing]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## What Are Tokens in LLMs? How Large Language Models Read, Count, and Process Text

文章解釋 LLM 中「令牌」(Token) 的基本概念及其實踐影響。令牌是文本的最小處理單位，不是完整詞彙，而是單字、詞碎片、標點、數字或空白；ChatGPT 及其他 AI 工具會將輸入分解為令牌序列處理。令牌計數與限制直接影響用戶體驗：「超過上下文視窗」「輸入過長」等錯誤源於令牌數量；模型容量規格（如 128K 令牌）定義可用上下文長度；費用按令牌計費，影響成本預算。理解令牌概念是現代 AI 素養基礎，有助用戶理解模型容量、價格與互動限制的來源。

### 重點
- 令牌定義：子詞單位（單字、詞碎片、標點、數字、空白或程式碼符號），非完整詞彙
- 上下文視窗與價格：令牌計數決定可用上下文長度與計費額度，限制模型輸入容量
- AI 素養：掌握令牌概念後，上下文限制、模型規格（128K tokens）、分層價格等行為變可理解

**原文：** [medium-tag-llm](https://medium.com/@amoljp19/what-are-tokens-in-llms-how-large-language-models-read-count-and-process-text-1a69a01b294a?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

If you&#x2019;ve ever used ChatGPT or another AI writing tool, you&#x2019;ve probably seen the word tokens. You might have noticed messages like: Continue reading on Medium »

</details>