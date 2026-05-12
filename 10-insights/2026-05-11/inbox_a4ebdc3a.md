---
id: inbox_a4ebdc3a
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/1800-infoq-architecture-netflix-serves-84-of-query-results-from-dc8f]]"
title: "Netflix Serves 84% of Query Results from Cache with Interval-Aware Caching in Apache Druid"
url: https://www.infoq.com/news/2026/05/netflix-druid-interval-cache/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-05-11T14:36:00+00:00
fetched_at: 2026-05-11T18:06:39.727758+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Netflix 通過區間感知緩存（Interval-Aware Caching）優化 Apache Druid 性能，使 84% 的分析查詢結果直接來自緩存，將查詢負載減少 33%。該方案的核心創新在於將滾動窗口查詢分解為可重用的時間段，使最新數據的重新計算與歷史數據的緩存重用實現靈活組合。在實時分析工作負載中，此優化策略有效降低了掃描量、改善了 P90 延遲，展示了時間序列數據緩存策略的實踐成果。"
key_points:
  - "84% 查詢結果來自緩存，查詢負載減少 33%，P90 延遲顯著改善"
  - "滾動窗口分解為可重用時間段，實現部分緩存重用和增量重新計算"
  - "時間序列數據的分層緩存策略，適用於實時分析工作負載"
tags: [caching-strategy, apache-druid, real-time-analytics, performance-optimization, time-series-cache]
topics: []
importance: 4
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Netflix Serves 84% of Query Results from Cache with Interval-Aware Caching in Apache Druid

Netflix 通過區間感知緩存（Interval-Aware Caching）優化 Apache Druid 性能，使 84% 的分析查詢結果直接來自緩存，將查詢負載減少 33%。該方案的核心創新在於將滾動窗口查詢分解為可重用的時間段，使最新數據的重新計算與歷史數據的緩存重用實現靈活組合。在實時分析工作負載中，此優化策略有效降低了掃描量、改善了 P90 延遲，展示了時間序列數據緩存策略的實踐成果。

### 重點
- 84% 查詢結果來自緩存，查詢負載減少 33%，P90 延遲顯著改善
- 滾動窗口分解為可重用時間段，實現部分緩存重用和增量重新計算
- 時間序列數據的分層緩存策略，適用於實時分析工作負載

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/05/netflix-druid-interval-cache/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Netflix improves Apache Druid performance with interval aware caching, serving 84% of analytics results from cache and reducing query load by 33%. The system decomposes rolling window queries into reusable time segments, enabling partial cache reuse and recomputation only for recent data. At scale, it reduces scan volume, improves P90 latency, and optimizes real time analytics workloads. By Leela Kumili

</details>