---
id: inbox_7599dc0e
date: 2026-05-21
source_ref: "[[00-inbox/.../inbox_7599dc0e]]"
title: "Bintrail: MySQL Time-Travel Queries Using Indexed Binlogs"
url: https://www.infoq.com/news/2026/05/bintrail-mysql-timetravel/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-05-21T17:03:00+00:00
fetched_at: 2026-05-22T01:00:20.452316+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Bintrail 是針對 MySQL 的新增層，透過 indexed binlogs 和 ProxySQL 實現 point-in-time queries 與 row-history lookups。MySQL 是主流關係型資料庫中唯一缺乏原生時間查詢的。Bintrail 無需修改 MySQL 或應用程式碼，支援查詢過去時間點的數據狀態和行級變更歷史，主要應用於資料恢復和審計。"
key_points:
  - "使用 indexed binlogs 和 ProxySQL 實現 point-in-time queries（無需修改 MySQL）"
  - "MySQL 是主流 RDBMS 中唯一缺乏原生時間查詢的"
  - "支援行級變更歷史查詢，應用於恢復和審計"
tags: [mysql, time-travel-queries, database-layer, binlogs]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Bintrail: MySQL Time-Travel Queries Using Indexed Binlogs

Bintrail 是針對 MySQL 的新增層，透過 indexed binlogs 和 ProxySQL 實現 point-in-time queries 與 row-history lookups。MySQL 是主流關係型資料庫中唯一缺乏原生時間查詢的。Bintrail 無需修改 MySQL 或應用程式碼，支援查詢過去時間點的數據狀態和行級變更歷史，主要應用於資料恢復和審計。

### 重點
- 使用 indexed binlogs 和 ProxySQL 實現 point-in-time queries（無需修改 MySQL）
- MySQL 是主流 RDBMS 中唯一缺乏原生時間查詢的
- 支援行級變更歷史查詢，應用於恢復和審計

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/05/bintrail-mysql-timetravel/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Bintrail: MySQL Time-Travel Queries Using Indexed Binlogs

Bintrail is a recently introduced layer that brings point-in-time queries and row-history lookups to MySQL, the only major relational database lacking native temporal querying. Using indexed binlogs behind ProxySQL and without modifying MySQL or application code, Bintrail supports querying data as of a past timestamp and reviewing change history, primarily for recovery and audit scenarios. By Renato Losio

</details>