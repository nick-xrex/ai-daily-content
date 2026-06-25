---
id: inbox_d7c3715e
date: 2026-06-25
source_ref: "[[00-inbox/2026-06-25/2200-medium-towards-data-science-vector-rag-isnt-enough-i-built-a-context-e40b]]"
title: "Vector RAG Isn’t Enough — I Built a Context Graph Layer for Multi-Agent Memory"
url: https://towardsdatascience.com/vector-rag-isnt-enough-i-built-a-context-graph-layer-for-multi-agent-memory/
source: medium-towards-data-science
published_at: 2026-06-25T18:37:53+00:00
fetched_at: 2026-06-25T22:14:46.448001+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者透過對同一組多 agent 對話集進行基準測試，對比原始聊天記錄、純向量 RAG 和 context graph 三種方案，發現純向量 RAG 在關係型檢索上存在顯著弱點。結果表明傳統向量檢索無法充分捕捉 agents 間的上下文依賴關係，需要圖結構層才能改善多 agent 記憶系統的精度和覆蓋率。"
key_points:
  - "向量 RAG 在多 agent 對話中的關係型檢索存在弱點（基準測試驗證）"
  - "Context graph 層相比純向量檢索顯著改善檢索精度和上下文連貫性"
  - "多 agent 系統需要結構化記憶層，單一向量索引不足"
tags: [rag-limitations, context-graph, multi-agent-memory, vector-retrieval]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Vector RAG Isn’t Enough — I Built a Context Graph Layer for Multi-Agent Memory

作者透過對同一組多 agent 對話集進行基準測試，對比原始聊天記錄、純向量 RAG 和 context graph 三種方案，發現純向量 RAG 在關係型檢索上存在顯著弱點。結果表明傳統向量檢索無法充分捕捉 agents 間的上下文依賴關係，需要圖結構層才能改善多 agent 記憶系統的精度和覆蓋率。

### 重點
- 向量 RAG 在多 agent 對話中的關係型檢索存在弱點（基準測試驗證）
- Context graph 層相比純向量檢索顯著改善檢索精度和上下文連貫性
- 多 agent 系統需要結構化記憶層，單一向量索引不足

**原文：** [medium-towards-data-science](https://towardsdatascience.com/vector-rag-isnt-enough-i-built-a-context-graph-layer-for-multi-agent-memory/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I benchmarked raw chat history, vector-only RAG, and a context graph on the same multi-agent conversations. The results exposed a surprising weakness in relational retrieval. 
 The post Vector RAG Isn’t Enough — I Built a Context Graph Layer for Multi-Agent Memory appeared first on Towards Data Science .

</details>