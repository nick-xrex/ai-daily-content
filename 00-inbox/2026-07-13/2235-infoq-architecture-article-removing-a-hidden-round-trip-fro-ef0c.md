---
id: inbox_a3049088
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/articles/aws-multi-region-signing/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Suresh Gururajan"
published_at: 2026-07-13T11:00:00+00:00
fetched_at: 2026-07-13T22:35:59.219525+00:00
content_hash: "ef0ce0e2898ce03b1019567b02fbaccaa6d4de1728d0ce1b9ced32346d1851c8"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: Removing a Hidden Round Trip from a Multi-Region AWS API

When a series of regional outages forced a rethink of a multi-region AWS API, the team discovered that an obstacle to global failover was hiding in plain sight: a pre-flight discovery call baked into every client session years earlier as the only available option. This article describes what it took to remove it, and what the rollout actually cost. By Suresh Gururajan