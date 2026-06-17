---
id: inbox_c05a965b
date: 2026-06-16
source_ref: "[[00-inbox/.../inbox_c05a965b]]"
title: "PostgreSQL 19 Beta Introduces SQL Graph Queries and Concurrent Table Repacking"
url: https://www.infoq.com/news/2026/06/postgresql-19-graph-queries/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-06-16T07:15:00+00:00
fetched_at: 2026-06-17T00:17:41.692029+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "PostgreSQL 19 Beta 版本發布，正式推出日期預計為 2026 年 9 月（遵循年度發布節奏）。新版本的主要創新包括原生 SQL Property Graph Queries（SQL/PGQ）支持，允許開發者直接在 SQL 中撰寫圖形查詢，而無需借助外部圖形資料庫。同時引入並發表重新打包（concurrent table repacking）功能，可在無停機狀態下回收儲存空間，解決了長期運行資料庫的儲存浪費問題。此外還包含多項性能最佳化、可觀測性改進和資料庫管理工具增強。"
key_points:
  - "PostgreSQL 19 Beta 發布，GA 預定 2026 年 9 月，支援原生 SQL/PGQ 圖形查詢"
  - "新增無停機並發表重新打包功能 (concurrent table repacking)，可動態回收儲存空間"
  - "包含性能、可觀測性和管理工具多項改進，支援更複雜的資料庫工作負載"
tags: [postgresql-19, sql-graph-queries, concurrent-repacking, storage-optimization, database]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## PostgreSQL 19 Beta Introduces SQL Graph Queries and Concurrent Table Repacking

PostgreSQL 19 Beta 版本發布，正式推出日期預計為 2026 年 9 月（遵循年度發布節奏）。新版本的主要創新包括原生 SQL Property Graph Queries（SQL/PGQ）支持，允許開發者直接在 SQL 中撰寫圖形查詢，而無需借助外部圖形資料庫。同時引入並發表重新打包（concurrent table repacking）功能，可在無停機狀態下回收儲存空間，解決了長期運行資料庫的儲存浪費問題。此外還包含多項性能最佳化、可觀測性改進和資料庫管理工具增強。

### 重點
- PostgreSQL 19 Beta 發布，GA 預定 2026 年 9 月，支援原生 SQL/PGQ 圖形查詢
- 新增無停機並發表重新打包功能 (concurrent table repacking)，可動態回收儲存空間
- 包含性能、可觀測性和管理工具多項改進，支援更複雜的資料庫工作負載

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/06/postgresql-19-graph-queries/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# PostgreSQL 19 Beta Introduces SQL Graph Queries and Concurrent Table Repacking

PostgreSQL 19 Beta has been announced, with general availability expected in September, following the project's yearly major-release cadence. This release introduces native SQL Property Graph Queries (SQL/PGQ), concurrent table repacking to reclaim storage without downtime, and a broad set of performance, observability, and administration improvements. By Renato Losio

</details>