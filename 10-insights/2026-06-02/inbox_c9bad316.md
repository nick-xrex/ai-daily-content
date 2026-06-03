---
id: inbox_c9bad316
date: 2026-06-02
source_ref: "[[00-inbox/2026-06-02/0030-medium-tag-llm-why-we-didnt-build-a-knowledge-graph-c308]]"
title: "Why We Didn’t Build a Knowledge Graph"
url: https://medium.com/@luo.junius/why-we-didnt-build-a-knowledge-graph-be19ca51225b?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-02T23:06:03+00:00
fetched_at: 2026-06-03T00:41:54.133338+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "企業文件 AI 系統 CogBase 選擇跳過傳統知識圖譜，改採向量儲存 + 結構化儲存 + LLM agent loop 的二層架構。此方案以 1/N 成本覆蓋知識圖譜約 80% 的功能，但權衡上在多跳推理 (6+ 跳) 和全域圖演算法上落後。團隊認為知識圖譜僅在三類場景值得建：安全關鍵性完整性 (藥物交互、詐欺偵測)、超長鏈推理 (6+ 跳規模)、全域圖演算法 (中心性、社群檢測)。"
key_points:
  - "二層架構：向量搜尋 + 結構化儲存 + agent loop，打敗知識圖譜的工程成本與維護負擔"
  - "多跳推理的臨界點：2–4 跳以內用 LLM 檢索效能接近；6+ 跳才需要圖結構"
  - "三類才建圖：(1) 安全關鍵完整性、(2) 超長推理鏈、(3) 全域演算法（無法在 context window 內計算）"
tags: [knowledge-graph, rag-architecture, agent-loop, document-ai, cost-tradeoff]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Why We Didn’t Build a Knowledge Graph

企業文件 AI 系統 CogBase 選擇跳過傳統知識圖譜，改採向量儲存 + 結構化儲存 + LLM agent loop 的二層架構。此方案以 1/N 成本覆蓋知識圖譜約 80% 的功能，但權衡上在多跳推理 (6+ 跳) 和全域圖演算法上落後。團隊認為知識圖譜僅在三類場景值得建：安全關鍵性完整性 (藥物交互、詐欺偵測)、超長鏈推理 (6+ 跳規模)、全域圖演算法 (中心性、社群檢測)。

### 重點
- 二層架構：向量搜尋 + 結構化儲存 + agent loop，打敗知識圖譜的工程成本與維護負擔
- 多跳推理的臨界點：2–4 跳以內用 LLM 檢索效能接近；6+ 跳才需要圖結構
- 三類才建圖：(1) 安全關鍵完整性、(2) 超長推理鏈、(3) 全域演算法（無法在 context window 內計算）

**原文：** [medium-tag-llm](https://medium.com/@luo.junius/why-we-didnt-build-a-knowledge-graph-be19ca51225b?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The honest case for skipping the graph in enterprise document AI &#x2014; and where a graph still wins Continue reading on Medium »

</details>