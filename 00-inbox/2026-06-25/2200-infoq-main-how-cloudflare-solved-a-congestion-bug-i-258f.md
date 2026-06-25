---
id: inbox_cefc800f
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/06/cloudflare-bug-quiche/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Gianmarco Nalin"
published_at: 2026-06-25T19:00:00+00:00
fetched_at: 2026-06-25T22:00:38.417008+00:00
content_hash: "258fadc8a19b627ae61f65453d0c6dad9ddbcf23fe3e32ac4d0d4e7be44d889c"
lang: en
caption_quality: None
raw: true
topics: []
---

# How Cloudflare Solved a Congestion Bug in quiche

Cloudflare has recently shared how they uncovered an issue in their Rust implementation of CUBIC, a congestion controller algorithm, which prevented it from recovering from a scenario of heavy packet loss at the start of a connection. By Gianmarco Nalin