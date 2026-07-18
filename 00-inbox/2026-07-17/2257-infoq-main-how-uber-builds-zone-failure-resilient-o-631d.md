---
id: inbox_628565af
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/07/uber-opensearch-zone-failure/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Claudio Masolo"
published_at: 2026-07-17T10:00:00+00:00
fetched_at: 2026-07-17T22:57:48.107399+00:00
content_hash: "631da3875a610b6f8ead30045427bd66b674018630e0b8dd2fd2a5abcde0af08"
lang: en
caption_quality: None
raw: true
topics: []
---

# How Uber Builds Zone-Failure-Resilient OpenSearch Clusters

Uber explained how it keeps its OpenSearch deployments running during a zone outage. It does this by using OpenSearch's built-in shard allocation and its own isolation-group system, which relies on the Odin container orchestration platform. This way, it maintains both query and ingestion capabilities. By Claudio Masolo