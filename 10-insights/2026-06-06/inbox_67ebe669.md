---
id: inbox_67ebe669
date: 2026-06-06
source_ref: "[[00-inbox/2026-06-06/0052-infoq-ai-ml-cloudflare-identifies-query-planning-bot-0724]]"
title: "Cloudflare Identifies Query Planning Bottleneck in ClickHouse"
url: https://www.infoq.com/news/2026/06/cloudflare-clickhouse-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-06-06T04:55:00+00:00
fetched_at: 2026-06-07T00:55:33.798697+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare 在其計費管道中發現 ClickHouse 查詢規劃階段存在性能瓶頸，根源為查詢規劃鎖的爭用。團隊通過性能分析實施了三項優化：(1) 將獨占鎖替換為共享鎖以減少爭用，(2) 移除每個查詢的 parts list 副本以降低內存開銷，(3) 改進 part filtering 邏輯。這些改變直接解決了計費管道的性能下降，展示了在高併發查詢場景下通過鎖粒度調整與數據結構優化提升數據庫性能的有效模式。"
key_points:
  - "ClickHouse 查詢規劃階段鎖爭用是 Cloudflare 計費管道性能瓶頸的根源"
  - "優化方案：獨占鎖→共享鎖、移除每查詢 parts list 副本、改進 part filtering，直接改善管道性能"
  - "高併發場景下通過鎖粒度細調與數據結構冗餘消除提升數據庫查詢效率的實戰案例"
tags: [clickhouse, performance, database-tuning]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Identifies Query Planning Bottleneck in ClickHouse

Cloudflare 在其計費管道中發現 ClickHouse 查詢規劃階段存在性能瓶頸，根源為查詢規劃鎖的爭用。團隊通過性能分析實施了三項優化：(1) 將獨占鎖替換為共享鎖以減少爭用，(2) 移除每個查詢的 parts list 副本以降低內存開銷，(3) 改進 part filtering 邏輯。這些改變直接解決了計費管道的性能下降，展示了在高併發查詢場景下通過鎖粒度調整與數據結構優化提升數據庫性能的有效模式。

### 重點
- ClickHouse 查詢規劃階段鎖爭用是 Cloudflare 計費管道性能瓶頸的根源
- 優化方案：獨占鎖→共享鎖、移除每查詢 parts list 副本、改進 part filtering，直接改善管道性能
- 高併發場景下通過鎖粒度細調與數據結構冗餘消除提升數據庫查詢效率的實戰案例

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/06/cloudflare-clickhouse-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cloudflare recently described how a slowdown in its billing pipeline was traced to contention inside the query planning stage of ClickHouse. The team profiled the bottleneck and patched ClickHouse to replace an exclusive lock with a shared lock, drop the per-query copy of the parts list, and improve part filtering. By Renato Losio

</details>