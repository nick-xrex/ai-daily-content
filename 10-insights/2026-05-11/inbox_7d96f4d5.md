---
id: inbox_7d96f4d5
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/1800-infoq-main-netflix-serves-84-of-query-results-from-61c7]]"
title: "Netflix Serves 84% of Query Results from Cache with Interval-Aware Caching in Apache Druid"
url: https://www.infoq.com/news/2026/05/netflix-druid-interval-cache/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-11T14:36:00+00:00
fetched_at: 2026-05-11T18:05:24.158077+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Netflix 透過開發區間感知快取機制改進 Apache Druid，使 84% 的分析查詢結果來自快取，整體查詢負載下降 33%。該系統將滾動窗口查詢分解為可重複使用的時間段，實現部分快取命中和增量重新計算，僅對最新數據進行重計算。此優化在大規模部署中顯著降低掃描量、改善 P90 延遲，並優化即時分析工作負荷。"
key_points:
  - "區間感知快取：滾動窗口查詢分解為可重用時間段，實現部分快取重用與增量重計算"
  - "量化成效：84% 查詢命中率、查詢負載 -33%、P90 延遲改善"
  - "適用場景：Apache Druid 即時分析規模化優化的通用模式"
tags: [apache-druid, caching-strategy, time-window-decomposition, analytics-optimization, netflix]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Netflix Serves 84% of Query Results from Cache with Interval-Aware Caching in Apache Druid

Netflix 透過開發區間感知快取機制改進 Apache Druid，使 84% 的分析查詢結果來自快取，整體查詢負載下降 33%。該系統將滾動窗口查詢分解為可重複使用的時間段，實現部分快取命中和增量重新計算，僅對最新數據進行重計算。此優化在大規模部署中顯著降低掃描量、改善 P90 延遲，並優化即時分析工作負荷。

### 重點
- 區間感知快取：滾動窗口查詢分解為可重用時間段，實現部分快取重用與增量重計算
- 量化成效：84% 查詢命中率、查詢負載 -33%、P90 延遲改善
- 適用場景：Apache Druid 即時分析規模化優化的通用模式

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/netflix-druid-interval-cache/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Netflix improves Apache Druid performance with interval aware caching, serving 84% of analytics results from cache and reducing query load by 33%. The system decomposes rolling window queries into reusable time segments, enabling partial cache reuse and recomputation only for recent data. At scale, it reduces scan volume, improves P90 latency, and optimizes real time analytics workloads. By Leela Kumili

</details>