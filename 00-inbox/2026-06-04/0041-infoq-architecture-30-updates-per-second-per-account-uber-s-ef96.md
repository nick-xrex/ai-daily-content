---
id: inbox_32fceb61
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/06/uber-payment-batching-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Leela Kumili"
published_at: 2026-06-04T14:02:00+00:00
fetched_at: 2026-06-05T00:41:02.692042+00:00
content_hash: "ef96c9e773bde69b38d46f2587bc1ab22e1b3328c68cfb0a52851efcd7f0aab2"
lang: en
caption_quality: None
raw: true
topics: []
---

# 30+ Updates per Second per Account: Uber Scales Ledger Processing with Batching

Uber introduced a high-throughput financial ledger processing system designed to handle hot account write contention at scale. Using 250ms batching, Redis coordination, and optimistic atomic updates, the system supports 30+ updates per second per account while preserving consistency and auditability, reducing multi-hour processing pipelines to minutes in its distributed accounting infrastructure. By Leela Kumili