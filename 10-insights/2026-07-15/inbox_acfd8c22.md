---
id: inbox_acfd8c22
date: 2026-07-15
source_ref: "[[00-inbox/.../inbox_acfd8c22]]"
title: "When RAG Should Stop Retrieving — Part 2: Building a Stopping Controller for Agentic RAG"
url: https://medium.com/@Neuraspark/when-rag-should-stop-retrieving-part-2-building-a-stopping-controller-for-agentic-rag-c82eda154b3c?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-07-15T16:08:42+00:00
fetched_at: 2026-07-16T02:07:13.719923+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "這是 RAG 停止條件系列的第二篇，探討在 agentic RAG 系統中何時應停止檢索。核心框架包含三個維度：覆蓋度（Coverage）、驗證（Verification）和一個「自欺騙編排迴圈」的控制機制。作為 Part 2，依賴 Part 1 的前置知識，但單篇仍缺乏完整的停止控制器設計方案、演算法細節和性能量化案例。"
key_points:
  - "在 agentic RAG 中定義檢索停止條件，涵蓋覆蓋度和驗證維度"
  - "透過編排迴圈機制避免 RAG 系統的自我欺騙（無限檢索）"
  - "系統級框架設計以平衡檢索充分性和成本效益"
tags: [rag, agentic-rag, retrieval-control, verification, orchestration]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 2
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## When RAG Should Stop Retrieving — Part 2: Building a Stopping Controller for Agentic RAG

這是 RAG 停止條件系列的第二篇，探討在 agentic RAG 系統中何時應停止檢索。核心框架包含三個維度：覆蓋度（Coverage）、驗證（Verification）和一個「自欺騙編排迴圈」的控制機制。作為 Part 2，依賴 Part 1 的前置知識，但單篇仍缺乏完整的停止控制器設計方案、演算法細節和性能量化案例。

### 重點
- 在 agentic RAG 中定義檢索停止條件，涵蓋覆蓋度和驗證維度
- 透過編排迴圈機制避免 RAG 系統的自我欺騙（無限檢索）
- 系統級框架設計以平衡檢索充分性和成本效益

**原文：** [medium-tag-llm](https://medium.com/@Neuraspark/when-rag-should-stop-retrieving-part-2-building-a-stopping-controller-for-agentic-rag-c82eda154b3c?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Neuraspark"
published_at: 2026-07-15T16:08:42+00:00
fetched_at: 2026-07-15T22:11:06.243901+00:00
content_hash: "1f2ce9e3e0215e34fc2886c87c9d83ce41831992a508f57b930ab61667d8279c"
lang: en
caption_quality: None
raw: true
topics: []
---

# When RAG Should Stop Retrieving — Part 2: Building a Stopping Controller for Agentic RAG

Coverage, verification, and an orchestration loop that can&#x2019;t fool itself. Continue reading on Medium »

</details>