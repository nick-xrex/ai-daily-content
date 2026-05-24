---
id: inbox_06274ed3
date: 2026-05-23
source_ref: "[[00-inbox/2026-05-23/0347-infoq-architecture-google-cloud-introduces-cross-engine-ice-4e18]]"
title: "Google Cloud Introduces Cross-Engine Iceberg Support in BigQuery"
url: https://www.infoq.com/news/2026/05/google-cross-engine-iceberg/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-05-23T08:42:00+00:00
fetched_at: 2026-05-24T03:52:19.748180+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google在Apache Iceberg Summit宣布BigQuery推出serverless Iceberg REST catalog預覽版。新功能支援使用者在BigQuery與Spark、Flink、Trino等引擎中建立、更新並查詢相同的Apache Iceberg表，無需複製數據。此舉打通多個計算引擎之間的數據共享，讓團隊可靈活選擇計算工具而不被數據孤島限制。"
key_points:
  - "BigQuery新增serverless Iceberg REST catalog預覽版，支援跨Spark/Flink/Trino等引擎查詢"
  - "相同表無需複製，降低存儲重複成本"
  - "基於Apache Iceberg開放標準，提升生態互操作性"
tags: [iceberg, bigquery, data-engineering, interoperability, cross-engine]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Google Cloud Introduces Cross-Engine Iceberg Support in BigQuery

Google在Apache Iceberg Summit宣布BigQuery推出serverless Iceberg REST catalog預覽版。新功能支援使用者在BigQuery與Spark、Flink、Trino等引擎中建立、更新並查詢相同的Apache Iceberg表，無需複製數據。此舉打通多個計算引擎之間的數據共享，讓團隊可靈活選擇計算工具而不被數據孤島限制。

### 重點
- BigQuery新增serverless Iceberg REST catalog預覽版，支援跨Spark/Flink/Trino等引擎查詢
- 相同表無需複製，降低存儲重複成本
- 基於Apache Iceberg開放標準，提升生態互操作性

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/05/google-cross-engine-iceberg/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

At the Apache Iceberg Summit last month, Google announced new interoperability features for Apache Iceberg in BigQuery. The preview of the serverless Iceberg REST catalog lets teams create, update, and query the same Apache Iceberg tables in BigQuery and in engines like Spark, Flink, and Trino without duplicating data. By Renato Losio

</details>