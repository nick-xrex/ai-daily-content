---
id: inbox_4d6467ed
date: 2026-06-06
source_ref: "[[00-inbox/2026-06-06/0052-infoq-architecture-cloudflare-identifies-query-planning-bot-0723]]"
title: "Cloudflare Identifies Query Planning Bottleneck in ClickHouse"
url: https://www.infoq.com/news/2026/06/cloudflare-clickhouse-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-06T04:55:00+00:00
fetched_at: 2026-06-07T00:56:24.438141+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare 識別出 ClickHouse 查詢規劃階段的效能瓶頸，導致計費 pipeline 速度下降。團隊透過效能分析並應用三項優化：1) 將 exclusive lock 替換為 shared lock，2) 移除每查詢的 parts list 副本，3) 改進 part filtering。此優化對大規模 OLAP 資料庫使用者具重要實務意義，可直接套用至類似工作負載。"
key_points:
  - "exclusive lock → shared lock：降低查詢規劃中的鎖定 contention"
  - "移除 per-query parts list copy：減少記憶體開銷與複製成本"
  - "改進 part filtering 邏輯：加速零件篩選效率"
tags: [clickhouse, query-optimization, database-performance, locking, infrastructure]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Identifies Query Planning Bottleneck in ClickHouse

Cloudflare 識別出 ClickHouse 查詢規劃階段的效能瓶頸，導致計費 pipeline 速度下降。團隊透過效能分析並應用三項優化：1) 將 exclusive lock 替換為 shared lock，2) 移除每查詢的 parts list 副本，3) 改進 part filtering。此優化對大規模 OLAP 資料庫使用者具重要實務意義，可直接套用至類似工作負載。

### 重點
- exclusive lock → shared lock：降低查詢規劃中的鎖定 contention
- 移除 per-query parts list copy：減少記憶體開銷與複製成本
- 改進 part filtering 邏輯：加速零件篩選效率

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/06/cloudflare-clickhouse-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cloudflare recently described how a slowdown in its billing pipeline was traced to contention inside the query planning stage of ClickHouse. The team profiled the bottleneck and patched ClickHouse to replace an exclusive lock with a shared lock, drop the per-query copy of the parts list, and improve part filtering. By Renato Losio

</details>