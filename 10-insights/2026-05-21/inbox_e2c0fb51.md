---
id: inbox_e2c0fb51
date: 2026-05-21
source_ref: "[[00-inbox/.../inbox_e2c0fb51]]"
title: "Bintrail: MySQL Time-Travel Queries Using Indexed Binlogs"
url: https://www.infoq.com/news/2026/05/bintrail-mysql-timetravel/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-21T17:03:00+00:00
fetched_at: 2026-05-22T00:59:16.315185+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Bintrail 是一個新興資料庫層，為 MySQL（目前唯一缺乏原生時間查詢的主流關聯式資料庫）帶來時間點查詢與行歷史查詢能力。使用 indexed binlogs 與 ProxySQL，無需修改 MySQL 或應用代碼即可支持查詢過去時間點的資料、審視變更歷史，主要應用於故障恢復與稽核場景。"
key_points:
  - "Bintrail 利用 indexed binlogs 實現時間旅行查詢"
  - "無需修改 MySQL 核心或應用程式代碼"
  - "適用於故障恢復與稽核需求"
tags: [database, mysql, temporal-queries]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Bintrail: MySQL Time-Travel Queries Using Indexed Binlogs

Bintrail 是一個新興資料庫層，為 MySQL（目前唯一缺乏原生時間查詢的主流關聯式資料庫）帶來時間點查詢與行歷史查詢能力。使用 indexed binlogs 與 ProxySQL，無需修改 MySQL 或應用代碼即可支持查詢過去時間點的資料、審視變更歷史，主要應用於故障恢復與稽核場景。

### 重點
- Bintrail 利用 indexed binlogs 實現時間旅行查詢
- 無需修改 MySQL 核心或應用程式代碼
- 適用於故障恢復與稽核需求

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/bintrail-mysql-timetravel/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Bintrail: MySQL Time-Travel Queries Using Indexed Binlogs

Bintrail is a recently introduced layer that brings point-in-time queries and row-history lookups to MySQL, the only major relational database lacking native temporal querying. Using indexed binlogs behind ProxySQL and without modifying MySQL or application code, Bintrail supports querying data as of a past timestamp and reviewing change history, primarily for recovery and audit scenarios. By Renato Losio

</details>