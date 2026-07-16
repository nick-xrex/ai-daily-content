---
id: inbox_7ae4228f
date: 2026-07-15
source_ref: "[[00-inbox/.../inbox_7ae4228f]]"
title: "Most RAG Hallucinations Are Retrieval Failures: How the Retrieval Brick Decides What the Model Can Invent"
url: https://towardsdatascience.com/most-rag-hallucinations-are-retrieval-failures-how-the-retrieval-brick-decides-what-the-model-can-invent/
source: medium-towards-data-science
published_at: 2026-07-15T12:00:00+00:00
fetched_at: 2026-07-16T02:05:38.320819+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "提出 RAG 系統中的 hallucination 問題本質源自 retrieval failures 而非模型本身的創造力失控。文章論述指出檢索層（retrieval brick）決定了模型能編造內容的邊界——若檢索結果正確，模型就無不正確資訊可用於生成幻覺。因此優化檢索品質（embedding、ranking、召回率）是消除 hallucination 的根本策略，這反映了 RAG 架構中垃圾進垃圾出的基本原理。"
key_points:
  - "RAG hallucination 本質是 garbage-in-garbage-out，源自檢索失敗而非模型缺陷"
  - "Retrieval brick 決定模型可能編造內容的邊界和方式"
  - "優化檢索品質（embedding、ranking、召回）是根本解決之道，比控制模型溫度更有效"
tags: [rag, hallucination, retrieval-optimization, enterprise-document-intelligence]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Most RAG Hallucinations Are Retrieval Failures: How the Retrieval Brick Decides What the Model Can Invent

提出 RAG 系統中的 hallucination 問題本質源自 retrieval failures 而非模型本身的創造力失控。文章論述指出檢索層（retrieval brick）決定了模型能編造內容的邊界——若檢索結果正確，模型就無不正確資訊可用於生成幻覺。因此優化檢索品質（embedding、ranking、召回率）是消除 hallucination 的根本策略，這反映了 RAG 架構中垃圾進垃圾出的基本原理。

### 重點
- RAG hallucination 本質是 garbage-in-garbage-out，源自檢索失敗而非模型缺陷
- Retrieval brick 決定模型可能編造內容的邊界和方式
- 優化檢索品質（embedding、ranking、召回）是根本解決之道，比控制模型溫度更有效

**原文：** [medium-towards-data-science](https://towardsdatascience.com/most-rag-hallucinations-are-retrieval-failures-how-the-retrieval-brick-decides-what-the-model-can-invent/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Most RAG Hallucinations Are Retrieval Failures: How the Retrieval Brick Decides What the Model Can Invent

Enterprise Document Intelligence [Vol.1 #7quinquies] - Hallucination is usually garbage-in. Fix retrieval, and the model has nothing left to make up 
 The post Most RAG Hallucinations Are Retrieval Failures: How the Retrieval Brick Decides What the Model Can Invent appeared first on Towards Data Science .

</details>