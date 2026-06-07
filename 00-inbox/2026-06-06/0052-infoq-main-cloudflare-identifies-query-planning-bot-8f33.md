---
id: inbox_7eb2a3d9
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/06/cloudflare-clickhouse-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Renato Losio"
published_at: 2026-06-06T04:55:00+00:00
fetched_at: 2026-06-07T00:52:23.006835+00:00
content_hash: "8f33763c373a0730b4f49b7770097544f2db78c07628df77486044491378fb14"
lang: en
caption_quality: None
raw: true
topics: []
---

# Cloudflare Identifies Query Planning Bottleneck in ClickHouse

Cloudflare recently described how a slowdown in its billing pipeline was traced to contention inside the query planning stage of ClickHouse. The team profiled the bottleneck and patched ClickHouse to replace an exclusive lock with a shared lock, drop the per-query copy of the parts list, and improve part filtering. By Renato Losio