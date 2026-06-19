---
id: inbox_86177d65
source: infoq-main
source_type: rss
url: "https://www.infoq.com/presentations/write-ahead-intent-log/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Vinay Chella, Akshat Goel"
published_at: 2026-06-18T13:13:00+00:00
fetched_at: 2026-06-18T22:00:41.722902+00:00
content_hash: "c1ed1e639ae1bfa52c67e60713288a8384dda739aa866c1469ebf8d15fbc2ee2"
lang: en
caption_quality: None
raw: true
topics: []
---

# Presentation: Write-Ahead Intent Log: A Foundation for Efficient CDC at Scale

Vinay Chella and Akshat Goel discuss the challenges of running traditional CDC across heterogeneous databases during peak order traffic. They explain how Debezium hit limits under high load and share how they built Write-Ahead Intent Log (WAIL) - a custom architecture that utilizes a dumb producer proxy and a smart consumer pattern to cleanly separate the intent from the state payload. By Vinay Chella, Akshat Goel