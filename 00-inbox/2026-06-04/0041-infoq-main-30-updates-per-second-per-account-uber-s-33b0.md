---
id: inbox_70b65de7
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/06/uber-payment-batching-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Leela Kumili"
published_at: 2026-06-04T14:02:00+00:00
fetched_at: 2026-06-05T00:41:00.748902+00:00
content_hash: "33b0c436560af2539cf6051e43a50ec519a86d8c4106f1ba0fc7ecdc31529d08"
lang: en
caption_quality: None
raw: true
topics: []
---

# 30+ Updates per Second per Account: Uber Scales Ledger Processing with Batching

Uber introduced a high-throughput financial ledger processing system designed to handle hot account write contention at scale. Using 250ms batching, Redis coordination, and optimistic atomic updates, the system supports 30+ updates per second per account while preserving consistency and auditability, reducing multi-hour processing pipelines to minutes in its distributed accounting infrastructure. By Leela Kumili