---
id: inbox_ec98f058
source: infoq-main
source_type: rss
url: "https://www.infoq.com/articles/schema-proliferation-problem/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Spoorthi Basu"
published_at: 2026-05-25T13:00:00+00:00
fetched_at: 2026-05-26T00:15:00.802193+00:00
content_hash: "315a4b664ce4a6f6e031b2df44081733f3f4c58523c70512b74eb6c204fa4b81"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: The Schema Proliferation Problem in Kafka and Flink Pipelines: How to Solve It

Schema proliferation builds slowly and gets expensive fast. One schema per event type feels right until there are ten tables, union queries spanning all of them, and a single field rename touching every schema. Discriminator-based schema consolidation collapses that to two tables, turning multi-table unions into a single query, while new variants are additive and don't break existing consumers. By Spoorthi Basu