---
id: inbox_fdd2cb6d
date: 2026-05-12
source_ref: "[[00-inbox/2026-05-12/1800-infoq-ai-ml-article-time-series-storage-design-choic-dd3e]]"
title: "Article: Time-Series Storage: Design Choices That Shape Cost and Performance"
url: https://www.infoq.com/articles/time-series-storage-design/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-05-12T09:00:00+00:00
fetched_at: 2026-05-12T18:05:54.378121+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "時間序列數據庫的成本和性能表現，主要取決於儲存設計決策（行佈局、壓縮、分區策略）而非數據庫選型本身。通過將序列身份規範化到獨立元數據表並以緊湊 ID 參考，可將儲存空間減少約 42%；高基數欄位（request ID、session token）應排除在序列身份外，以免規範化收益崩塌；時間分區配合序列身份雙軸分區，實現 O(1) 資料過期和寫入分散；由 5 秒解析度降採樣至 1 小時可減少 720 倍行數，同時保留近期全解析度、歷史查詢使用預聚合回滾。該文使用 PostgreSQL 和 Apache Parquet 實驗驗證各項 trade-off，並提供 Key Takeaways。"
key_points:
  - "序列身份規範化減少約 42% 儲存空間：將維度字符串集中存放一次，每行只存緊湊整數 ID，避免重複存儲 device name、region 等"
  - "高基數欄位（request ID、session token）應從序列身份排除，否則規範化收益崩塌且儲存和索引成本線性增長"
  - "時間 + 序列身份雙軸分區分散寫熱點，配合 5 秒→1 小時降採樣可減少 720 倍行數，保留近期全分辨率"
tags: [time-series-database, storage-design, data-partitioning, cost-optimization, postgresql-parquet]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: Time-Series Storage: Design Choices That Shape Cost and Performance

時間序列數據庫的成本和性能表現，主要取決於儲存設計決策（行佈局、壓縮、分區策略）而非數據庫選型本身。通過將序列身份規範化到獨立元數據表並以緊湊 ID 參考，可將儲存空間減少約 42%；高基數欄位（request ID、session token）應排除在序列身份外，以免規範化收益崩塌；時間分區配合序列身份雙軸分區，實現 O(1) 資料過期和寫入分散；由 5 秒解析度降採樣至 1 小時可減少 720 倍行數，同時保留近期全解析度、歷史查詢使用預聚合回滾。該文使用 PostgreSQL 和 Apache Parquet 實驗驗證各項 trade-off，並提供 Key Takeaways。

### 重點
- 序列身份規範化減少約 42% 儲存空間：將維度字符串集中存放一次，每行只存緊湊整數 ID，避免重複存儲 device name、region 等
- 高基數欄位（request ID、session token）應從序列身份排除，否則規範化收益崩塌且儲存和索引成本線性增長
- 時間 + 序列身份雙軸分區分散寫熱點，配合 5 秒→1 小時降採樣可減少 720 倍行數，保留近期全分辨率

**原文：** [infoq-ai-ml](https://www.infoq.com/articles/time-series-storage-design/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Every time-series database makes a set of storage design decisions: how to lay out rows, when to compress, what to partition on. These decisions determine cost and query performance more than the choice of database itself. This article works through those fundamentals from first principles, using widely available tools like PostgreSQL and Apache Parquet to make each trade-off measurable. By Nirmesh Khandelwal

</details>