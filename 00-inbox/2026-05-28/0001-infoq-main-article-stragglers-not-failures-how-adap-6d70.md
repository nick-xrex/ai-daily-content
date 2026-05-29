---
id: inbox_ea6be90d
source: infoq-main
source_type: rss
url: "https://www.infoq.com/articles/adaptive-hedged-requests-p99-latency/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Prathamesh Bhope"
published_at: 2026-05-28T09:00:00+00:00
fetched_at: 2026-05-29T00:01:04.023190+00:00
content_hash: "6d7056020b1c5e022c38f26e9ce85aa673090f324dd61d7218a50e9ef3b97974"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: Stragglers, Not Failures: How Adaptive Hedged Requests Reduce p99 Latency by 74 Percent

n fan-out microservice architectures, slow-but-completing requests accumulate across services and drive p99 latency far higher than per-service metrics suggest. This article presents an adaptive hedging mechanism that uses DDSketch for real-time quantile estimation, windowed rotation to handle distribution drift, and a token-bucket budget to prevent load amplification. By Prathamesh Bhope