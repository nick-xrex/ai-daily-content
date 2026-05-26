---
id: inbox_d3c7fbdd
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/articles/schema-proliferation-problem/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Spoorthi Basu"
published_at: 2026-05-25T13:00:00+00:00
fetched_at: 2026-05-26T00:15:02.382482+00:00
content_hash: "e35dda8d0647d05f4e8ed6db57586656ec76fbe5afe379a28f5d5f51a0c0036f"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: The Schema Proliferation Problem in Kafka and Flink Pipelines: How to Solve It

Schema proliferation builds slowly and gets expensive fast. One schema per event type feels right until there are ten tables, union queries spanning all of them, and a single field rename touching every schema. Discriminator-based schema consolidation collapses that to two tables, turning multi-table unions into a single query, while new variants are additive and don't break existing consumers. By Spoorthi Basu