---
id: inbox_a0ff295f
date: 2026-05-28
source_ref: "[[00-inbox/2026-05-28/0001-infoq-architecture-article-stragglers-not-failures-how-adap-fb73]]"
title: "Article: Stragglers, Not Failures: How Adaptive Hedged Requests Reduce p99 Latency by 74 Percent"
url: https://www.infoq.com/articles/adaptive-hedged-requests-p99-latency/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-05-28T09:00:00+00:00
fetched_at: 2026-05-29T00:10:07.483353+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: ""
key_points:
tags: []
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: Stragglers, Not Failures: How Adaptive Hedged Requests Reduce p99 Latency by 74 Percent



### 重點

**原文：** [infoq-architecture](https://www.infoq.com/articles/adaptive-hedged-requests-p99-latency/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

n fan-out microservice architectures, slow-but-completing requests accumulate across services and drive p99 latency far higher than per-service metrics suggest. This article presents an adaptive hedging mechanism that uses DDSketch for real-time quantile estimation, windowed rotation to handle distribution drift, and a token-bucket budget to prevent load amplification. By Prathamesh Bhope

</details>