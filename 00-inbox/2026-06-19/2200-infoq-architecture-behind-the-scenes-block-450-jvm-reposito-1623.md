---
id: inbox_0d4d5df4
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/06/block-450-jvm-monorepo-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Leela Kumili"
published_at: 2026-06-19T14:47:00+00:00
fetched_at: 2026-06-19T22:00:42.001231+00:00
content_hash: "16236c3d79b9f5e21be5b5d6ba380e644a3cf21529589af8bc44c02acbf15b1f"
lang: en
caption_quality: None
raw: true
topics: []
---

# Behind the Scenes: Block 450 JVM Repositories Into Monorepo to Reduce Dependency Drift

Block, Inc. describes migrating ~450 JVM repositories into a monorepo across Cash App and Square engineering to reduce dependency drift and coordination overhead. The system supports ~8,800 weekly builds with ~10 min p90 CI time. The approach improves cross-service changes, build visibility, and developer experience through dependency graph–based builds, selective CI, and custom IDE tooling. By Leela Kumili