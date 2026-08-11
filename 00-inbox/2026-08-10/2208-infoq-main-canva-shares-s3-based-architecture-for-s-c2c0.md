---
id: inbox_50b51adb
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/08/canva-session-revocation-scale/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Leela Kumili"
published_at: 2026-08-10T14:14:00+00:00
fetched_at: 2026-08-10T22:08:45.779619+00:00
content_hash: "c2c0c95a8280930c66f8fd3319ac4de90f22ef62b5935480e0d06bf1e96c909c"
lang: en
caption_quality: None
raw: true
topics: []
---

# Canva Shares S3 Based Architecture for Session Revocation Across Hundreds of Millions of Sessions

Canva redesigned session revocation infrastructure to support 100M active sessions while reducing database lookups. The architecture uses Amazon S3 for durable revocation records and distributes compact, in-memory indexes to application gateways. Canva said the design improved deployment speed, reduced database infrastructure requirements, and cut the revocation cache memory footprint by 87.5%. By Leela Kumili