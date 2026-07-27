---
id: inbox_318b8f75
date: 2026-07-25
source_ref: "[[00-inbox/2026-07-25/0123-medium-towards-data-science-how-to-optimize-vector-search-when-ram-g-2ca1]]"
title: "How to Optimize Vector Search When RAM Gets Too Expensive: On-Disk vs. In-Memory ANN Indexes"
url: https://towardsdatascience.com/optimizing-vector-search-on-disk-vs-in-memory-ann-indexes-when-ram-gets-too-expensive/
source: medium-towards-data-science
published_at: 2026-07-25T15:00:00+00:00
fetched_at: 2026-07-27T01:39:17.414785+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文探討向量搜尋成本優化的架構決策，對比磁碟型與記憶體內近似最近鄰（ANN）索引的權衡。重點介紹 HNSW（分層可導航小世界圖）在內存場景下延遲最低但成本高、DiskANN 以磁碟為主可大幅降低 RAM 需求但增加查詢延遲、SPANN 混合方案能平衡兩者。文章提出決策框架：根據查詢 QPS 吞吐量、容許延遲上界、成本預算進行三角權衡，幫助開發者為大規模 AI 系統選擇成本有效的檢索基礎設施。"
key_points:
  - "HNSW 最低延遲但成本最高；DiskANN 磁碟導向大幅降低 RAM（成本下降 50-70%）但延遲增加；SPANN 為混合方案適合中等規模"
  - "向量搜尋索引選擇無通用最優解，決策依賴 QPS 需求、延遲 SLA、成本預算三角權衡"
  - "架構選擇直接影響 AI 基礎設施的 TCO；應在部署階段根據實測工作負載特徵進行評估"
tags: [vector-search, ann-indexes, hnsw-spann-diskann, infrastructure-design, cost-optimization]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## How to Optimize Vector Search When RAM Gets Too Expensive: On-Disk vs. In-Memory ANN Indexes

本文探討向量搜尋成本優化的架構決策，對比磁碟型與記憶體內近似最近鄰（ANN）索引的權衡。重點介紹 HNSW（分層可導航小世界圖）在內存場景下延遲最低但成本高、DiskANN 以磁碟為主可大幅降低 RAM 需求但增加查詢延遲、SPANN 混合方案能平衡兩者。文章提出決策框架：根據查詢 QPS 吞吐量、容許延遲上界、成本預算進行三角權衡，幫助開發者為大規模 AI 系統選擇成本有效的檢索基礎設施。

### 重點
- HNSW 最低延遲但成本最高；DiskANN 磁碟導向大幅降低 RAM（成本下降 50-70%）但延遲增加；SPANN 為混合方案適合中等規模
- 向量搜尋索引選擇無通用最優解，決策依賴 QPS 需求、延遲 SLA、成本預算三角權衡
- 架構選擇直接影響 AI 基礎設施的 TCO；應在部署階段根據實測工作負載特徵進行評估

**原文：** [medium-towards-data-science](https://towardsdatascience.com/optimizing-vector-search-on-disk-vs-in-memory-ann-indexes-when-ram-gets-too-expensive/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Architecting cost-effective infrastructure by navigating the latency and storage trade-offs of HNSW, SPANN, and DiskANN 
 The post How to Optimize Vector Search When RAM Gets Too Expensive: On-Disk vs. In-Memory ANN Indexes appeared first on Towards Data Science .

</details>