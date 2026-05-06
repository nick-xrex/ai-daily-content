---
id: inbox_ac7b70af
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1251-medium-tag-ai-day-2-choosing-the-stack-under-constrain-6ca4]]"
title: "Day 2 — Choosing the Stack Under Constraints"
url: https://medium.com/@jk.devfreelancer/day-2-choosing-the-stack-under-constraints-2f3f09db268e?source=rss------artificial_intelligence-5
source: medium-tag-ai
published_at: 2026-05-06T12:31:01+00:00
fetched_at: 2026-05-06T12:58:06.123480+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "記錄在嚴格成本約束下構建 AI 驅動文檔搜尋系統的技術棧選擇。選用 Gemini embedding 模型、ChromaDB 向量數據庫、Gemini 2.5 Flash 語言模型、LangChain 框架與 Google Colab 開發環境，在 API 速率限制、Colab 會話持久化問題、與 ChromaDB 生產擴展限制間進行權衡。展示「快速迭代優於完美」的務實策略。"
key_points:
  - "在「免費或低成本工具優先」約束下，選用 Gemini embedding + ChromaDB + LangChain 組合"
  - "面臨 API 速率限制、Colab 持久化問題、與 ChromaDB 生產級擴展限制三重權衡"
  - "優先追求快速原型與迭代，犧牲完美度與生產級可靠性"
tags: [cost-constrained-stack, gemini-embedding, langchain-rag]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Day 2 — Choosing the Stack Under Constraints

記錄在嚴格成本約束下構建 AI 驅動文檔搜尋系統的技術棧選擇。選用 Gemini embedding 模型、ChromaDB 向量數據庫、Gemini 2.5 Flash 語言模型、LangChain 框架與 Google Colab 開發環境，在 API 速率限制、Colab 會話持久化問題、與 ChromaDB 生產擴展限制間進行權衡。展示「快速迭代優於完美」的務實策略。

### 重點
- 在「免費或低成本工具優先」約束下，選用 Gemini embedding + ChromaDB + LangChain 組合
- 面臨 API 速率限制、Colab 持久化問題、與 ChromaDB 生產級擴展限制三重權衡
- 優先追求快速原型與迭代，犧牲完美度與生產級可靠性

**原文：** [medium-tag-ai](https://medium.com/@jk.devfreelancer/day-2-choosing-the-stack-under-constraints-2f3f09db268e?source=rss------artificial_intelligence-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@jk.devfreelancer/day-2-choosing-the-stack-under-constraints-2f3f09db268e?source=rss------artificial_intelligence-5"><img src="https://cdn-images-1.medium.com/max/1536/1*W2zbNm4Pyjf29l8Hn3VRNg.png" width="1536" /></a></p><p class="medium-feed-snippet">After breaking the documents into chunks on Day 1, the next question was obvious:</p><p class="medium-feed-link"><a href="https://medium.com/@jk.devfreelancer/day-2-choosing-the-stack-under-constraints-2f3f09db268e?source=rss------artificial_intelligence-5">Continue reading on Medium »</a></p></div>

</details>