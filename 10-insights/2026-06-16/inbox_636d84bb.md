---
id: inbox_636d84bb
date: 2026-06-16
source_ref: "[[00-inbox/2026-06-16/2200-infoq-main-postgresql-19-beta-introduces-sql-graph-c482]]"
title: "PostgreSQL 19 Beta Introduces SQL Graph Queries and Concurrent Table Repacking"
url: https://www.infoq.com/news/2026/06/postgresql-19-graph-queries/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-16T07:15:00+00:00
fetched_at: 2026-06-16T22:10:50.945509+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "PostgreSQL 項目於六月宣佈推出版本 19 的測試版，預計九月達成正式上市，保持其年度主版本發布週期。此版本重點特性包括原生 SQL Property Graph 查詢支持（SQL/PGQ），允許開發者用標準 SQL 直接表達圖論邏輯。傳統方式下複雜圖遍歷和關係查詢需借助應用層代碼或非標準擴展。新的 SQL/PGQ 功能簡化了這些操作，提升了查詢可讀性和效率。另一項重要改進是並發表空間重組（Concurrent Table Repacking），能在無需停機的情況下回收因刪除操作產生的碎片存儲。此外 PostgreSQL 19 涵蓋性能、可觀測性及管理工具的廣泛改進。"
key_points:
  - "SQL/PGQ 原生圖查詢支持，簡化複雜圖論邏輯的 SQL 語法表達"
  - "並發表空間重組實現零停機的存儲碎片回收機制"
  - "預計九月 GA，涵蓋性能、可觀測性與管理工具廣泛改進"
tags: [postgresql, database, graph-queries, sql-pgq, storage]
topics: []
importance: 3
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## PostgreSQL 19 Beta Introduces SQL Graph Queries and Concurrent Table Repacking

PostgreSQL 項目於六月宣佈推出版本 19 的測試版，預計九月達成正式上市，保持其年度主版本發布週期。此版本重點特性包括原生 SQL Property Graph 查詢支持（SQL/PGQ），允許開發者用標準 SQL 直接表達圖論邏輯。傳統方式下複雜圖遍歷和關係查詢需借助應用層代碼或非標準擴展。新的 SQL/PGQ 功能簡化了這些操作，提升了查詢可讀性和效率。另一項重要改進是並發表空間重組（Concurrent Table Repacking），能在無需停機的情況下回收因刪除操作產生的碎片存儲。此外 PostgreSQL 19 涵蓋性能、可觀測性及管理工具的廣泛改進。

### 重點
- SQL/PGQ 原生圖查詢支持，簡化複雜圖論邏輯的 SQL 語法表達
- 並發表空間重組實現零停機的存儲碎片回收機制
- 預計九月 GA，涵蓋性能、可觀測性與管理工具廣泛改進

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/postgresql-19-graph-queries/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

PostgreSQL 19 Beta has been announced, with general availability expected in September, following the project's yearly major-release cadence. This release introduces native SQL Property Graph Queries (SQL/PGQ), concurrent table repacking to reclaim storage without downtime, and a broad set of performance, observability, and administration improvements. By Renato Losio

</details>