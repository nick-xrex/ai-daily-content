---
id: inbox_67ebe669
source: infoq-ai-ml
source_type: rss
url: "https://www.infoq.com/news/2026/06/cloudflare-clickhouse-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering"
author: "Renato Losio"
published_at: 2026-06-06T04:55:00+00:00
fetched_at: 2026-06-07T00:52:23.769513+00:00
content_hash: "0724a9ada24888f1e52fcb4bc31c983c18cc4c09aed31966f25fec2e7793b21b"
lang: en
caption_quality: None
raw: true
topics: []
---

# Cloudflare Identifies Query Planning Bottleneck in ClickHouse

Cloudflare recently described how a slowdown in its billing pipeline was traced to contention inside the query planning stage of ClickHouse. The team profiled the bottleneck and patched ClickHouse to replace an exclusive lock with a shared lock, drop the per-query copy of the parts list, and improve part filtering. By Renato Losio