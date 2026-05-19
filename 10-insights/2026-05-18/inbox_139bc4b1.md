---
id: inbox_139bc4b1
date: 2026-05-18
source_ref: "[[00-inbox/.../inbox_139bc4b1]]"
title: "Swiggy Improves Search Autocomplete Using Real Time Machine Learning Ranking"
url: https://www.infoq.com/news/2026/05/swiggy-autocomplete-rt-ranking/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-05-18T14:38:00+00:00
fetched_at: 2026-05-19T02:28:32.900001+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Swiggy 詳細發布其實時 ML 排序系統，用於改善搜尋自動完成功能的相關性。系統架構分離候選生成和排序兩個階段，使用 OpenSearch 作為候選庫、feature stores 提供實時信號、learning-to-rank 模型替代傳統啟發式排序法。架構嚴格控制端對端延遲以支持毫秒級回應，同時支持基於用戶行為信號的連續模型更新無需停機。該分層架構已成為工業級搜尋排序系統的通用模式，廣泛應用於電商、外賣、社交等高流量平台。"
key_points:
  - "Swiggy 採用 OpenSearch + feature stores + learning-to-rank 三層組合，用實時 ML 替代啟發式排序"
  - "架構分為候選生成和排序兩層，獨立優化每層以降低端對端延遲，支持毫秒級查詢響應"
  - "支持基於用戶行為信號的連續模型更新，無需停機發布新版本，實現 24/7 自適應排序"
tags: [ml-ranking, learning-to-rank, feature-stores, opensearch]
topics: []
importance: 2
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Swiggy Improves Search Autocomplete Using Real Time Machine Learning Ranking

Swiggy 詳細發布其實時 ML 排序系統，用於改善搜尋自動完成功能的相關性。系統架構分離候選生成和排序兩個階段，使用 OpenSearch 作為候選庫、feature stores 提供實時信號、learning-to-rank 模型替代傳統啟發式排序法。架構嚴格控制端對端延遲以支持毫秒級回應，同時支持基於用戶行為信號的連續模型更新無需停機。該分層架構已成為工業級搜尋排序系統的通用模式，廣泛應用於電商、外賣、社交等高流量平台。

### 重點
- Swiggy 採用 OpenSearch + feature stores + learning-to-rank 三層組合，用實時 ML 替代啟發式排序
- 架構分為候選生成和排序兩層，獨立優化每層以降低端對端延遲，支持毫秒級查詢響應
- 支持基於用戶行為信號的連續模型更新，無需停機發布新版本，實現 24/7 自適應排序

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/05/swiggy-autocomplete-rt-ranking/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Swiggy Improves Search Autocomplete Using Real Time Machine Learning Ranking

Swiggy detailed real-time machine-learning ranking system for autocomplete built on OpenSearch. The architecture separates candidate generation and ranking, uses feature stores for real time signals, and applies learning to rank models for improved relevance. It replaces heuristic ranking while maintaining strict latency constraints and enabling continuous model updates from user behavior signals. By Leela Kumili

</details>