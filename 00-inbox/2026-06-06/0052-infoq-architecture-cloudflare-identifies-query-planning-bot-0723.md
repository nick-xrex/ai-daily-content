---
id: inbox_4d6467ed
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/06/cloudflare-clickhouse-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Renato Losio"
published_at: 2026-06-06T04:55:00+00:00
fetched_at: 2026-06-07T00:52:24.554919+00:00
content_hash: "072356afe51587d5c8051f0f1d048a0d83e53f2f0bd8bfec64278d9d64ea4122"
lang: en
caption_quality: None
raw: true
topics: []
---

# Cloudflare Identifies Query Planning Bottleneck in ClickHouse

Cloudflare recently described how a slowdown in its billing pipeline was traced to contention inside the query planning stage of ClickHouse. The team profiled the bottleneck and patched ClickHouse to replace an exclusive lock with a shared lock, drop the per-query copy of the parts list, and improve part filtering. By Renato Losio