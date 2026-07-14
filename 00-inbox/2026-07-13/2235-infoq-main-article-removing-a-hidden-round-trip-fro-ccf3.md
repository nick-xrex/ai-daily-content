---
id: inbox_60b1ca99
source: infoq-main
source_type: rss
url: "https://www.infoq.com/articles/aws-multi-region-signing/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Suresh Gururajan"
published_at: 2026-07-13T11:00:00+00:00
fetched_at: 2026-07-13T22:35:57.525644+00:00
content_hash: "ccf31f593d97277b079bac82a09695a4de4a39a72cb83ff5abffa5b73c7fa4ec"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: Removing a Hidden Round Trip from a Multi-Region AWS API

When a series of regional outages forced a rethink of a multi-region AWS API, the team discovered that an obstacle to global failover was hiding in plain sight: a pre-flight discovery call baked into every client session years earlier as the only available option. This article describes what it took to remove it, and what the rollout actually cost. By Suresh Gururajan