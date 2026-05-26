---
id: inbox_d3c7fbdd
date: 2026-05-25
source_ref: "[[00-inbox/2026-05-25/0015-infoq-architecture-article-the-schema-proliferation-problem-e35d]]"
title: "Article: The Schema Proliferation Problem in Kafka and Flink Pipelines: How to Solve It"
url: https://www.infoq.com/articles/schema-proliferation-problem/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-05-25T13:00:00+00:00
fetched_at: 2026-05-26T00:28:11.642244+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章指出 Kafka 與 Flink pipeline 中 schema 激增問題：隨著事件類型增多，多表 union 查詢與欄位重命名變得維護困難且昂貴。提案採用 discriminator-based schema consolidation，將多個 schema 合併為兩個表加一個單一查詢，新增變體只需添加新記錄而無須修改現有 consumer。此方案以簡化查詢與向後相容性著稱。"
key_points:
  - "Discriminator 型式合併將多表 union 簡化為單一查詢"
  - "新變體採行為添加式而非破壞式修改，保護既有 consumer"
  - "解決 schema 蔓延導致的維護成本爆增問題"
tags: [schema-design, kafka, flink, data-pipeline, schema-consolidation]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: The Schema Proliferation Problem in Kafka and Flink Pipelines: How to Solve It

文章指出 Kafka 與 Flink pipeline 中 schema 激增問題：隨著事件類型增多，多表 union 查詢與欄位重命名變得維護困難且昂貴。提案採用 discriminator-based schema consolidation，將多個 schema 合併為兩個表加一個單一查詢，新增變體只需添加新記錄而無須修改現有 consumer。此方案以簡化查詢與向後相容性著稱。

### 重點
- Discriminator 型式合併將多表 union 簡化為單一查詢
- 新變體採行為添加式而非破壞式修改，保護既有 consumer
- 解決 schema 蔓延導致的維護成本爆增問題

**原文：** [infoq-architecture](https://www.infoq.com/articles/schema-proliferation-problem/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Schema proliferation builds slowly and gets expensive fast. One schema per event type feels right until there are ten tables, union queries spanning all of them, and a single field rename touching every schema. Discriminator-based schema consolidation collapses that to two tables, turning multi-table unions into a single query, while new variants are additive and don't break existing consumers. By Spoorthi Basu

</details>