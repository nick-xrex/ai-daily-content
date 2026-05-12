---
id: inbox_a4ebdc3a
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/05/netflix-druid-interval-cache/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Leela Kumili"
published_at: 2026-05-11T14:36:00+00:00
fetched_at: 2026-05-11T18:00:33.361847+00:00
content_hash: "dc8fd4e527d015a014aee9fe14eb46e537e91718df1831b92df9601f0b55eefb"
lang: en
caption_quality: None
raw: true
topics: []
---

# Netflix Serves 84% of Query Results from Cache with Interval-Aware Caching in Apache Druid

Netflix improves Apache Druid performance with interval aware caching, serving 84% of analytics results from cache and reducing query load by 33%. The system decomposes rolling window queries into reusable time segments, enabling partial cache reuse and recomputation only for recent data. At scale, it reduces scan volume, improves P90 latency, and optimizes real time analytics workloads. By Leela Kumili