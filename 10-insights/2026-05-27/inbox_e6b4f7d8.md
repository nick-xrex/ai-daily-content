---
id: inbox_e6b4f7d8
date: 2026-05-27
source_ref: "[[00-inbox/2026-05-27/2345-medium-tag-llm-stop-trusting-the-embedding-how-real-rag-37cc]]"
title: "Stop Trusting the Embedding: How Real RAG Pipelines Actually Work"
url: https://medium.com/@el_mohamad/stop-trusting-the-embedding-how-real-rag-pipelines-actually-work-6d1dd7a9143f?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-27T18:37:43+00:00
fetched_at: 2026-05-27T23:57:22.631410+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "詳細剖析真實 RAG（檢索增強生成）系統的 3 個常見初期失誤：(1) 無量化評估導致品質不明（60% 或 95% 皆可能）；(2) 盲目堆砌技術（HyDE、重排序、查詢改寫）不知哪個有效；(3) 把 embedding 當魔法、忽視關鍵字搜尋和重排序。該文倡導從第一天起建立完整 4 層 pipeline（檢索層 + hybrid search + contextual retrieval + reranking），透過分層對比測試選擇有效技巧，修復這三項後典型系統能從 60% 躍升至 95%+ 檢索精度。"
key_points:
  - "RAG 系統初期 3 大問題：無基準評估、技術亂堆砌（不知何者起效）、過度信賴 embedding 忽視關鍵字+重排序"
  - "4 層完整 pipeline：(1) 文本分塊策略 (2) contextual retrieval（按上下文而非單一 embedding 檢索） (3) hybrid search（向量+關鍵字） (4) reranking；修復後精度 60%→95%+"
  - "檢索精度瓶頸常不在 embedding 本身，而在前置分塊、上下文理解、與重排序層；實踐應對每層進行 A/B 測試而非猜測"
tags: [rag, retrieval-augmented-generation, embedding, hybrid-search]
topics: []
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Stop Trusting the Embedding: How Real RAG Pipelines Actually Work

詳細剖析真實 RAG（檢索增強生成）系統的 3 個常見初期失誤：(1) 無量化評估導致品質不明（60% 或 95% 皆可能）；(2) 盲目堆砌技術（HyDE、重排序、查詢改寫）不知哪個有效；(3) 把 embedding 當魔法、忽視關鍵字搜尋和重排序。該文倡導從第一天起建立完整 4 層 pipeline（檢索層 + hybrid search + contextual retrieval + reranking），透過分層對比測試選擇有效技巧，修復這三項後典型系統能從 60% 躍升至 95%+ 檢索精度。

### 重點
- RAG 系統初期 3 大問題：無基準評估、技術亂堆砌（不知何者起效）、過度信賴 embedding 忽視關鍵字+重排序
- 4 層完整 pipeline：(1) 文本分塊策略 (2) contextual retrieval（按上下文而非單一 embedding 檢索） (3) hybrid search（向量+關鍵字） (4) reranking；修復後精度 60%→95%+
- 檢索精度瓶頸常不在 embedding 本身，而在前置分塊、上下文理解、與重排序層；實踐應對每層進行 A/B 測試而非猜測

**原文：** [medium-tag-llm](https://medium.com/@el_mohamad/stop-trusting-the-embedding-how-real-rag-pipelines-actually-work-6d1dd7a9143f?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A few years ago, getting a model to answer questions about your own data was simple. You wrote the FAQs into the system prompt, you wrote&#x2026; Continue reading on Medium »

</details>