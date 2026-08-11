---
id: inbox_29a11293
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/08/canva-session-revocation-scale/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Leela Kumili"
published_at: 2026-08-10T14:14:00+00:00
fetched_at: 2026-08-10T22:08:47.674442+00:00
content_hash: "bf15554bd02b002b5a29bd10f6ff5d8ea8ccc2bd870c128d92670f93c0c43b57"
lang: en
caption_quality: None
raw: true
topics: []
---

# Canva Shares S3 Based Architecture for Session Revocation Across Hundreds of Millions of Sessions

Canva redesigned session revocation infrastructure to support 100M active sessions while reducing database lookups. The architecture uses Amazon S3 for durable revocation records and distributes compact, in-memory indexes to application gateways. Canva said the design improved deployment speed, reduced database infrastructure requirements, and cut the revocation cache memory footprint by 87.5%. By Leela Kumili