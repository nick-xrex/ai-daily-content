---
id: inbox_ea6be90d
date: 2026-05-28
source_ref: "[[00-inbox/2026-05-28/0001-infoq-main-article-stragglers-not-failures-how-adap-6d70]]"
title: "Article: Stragglers, Not Failures: How Adaptive Hedged Requests Reduce p99 Latency by 74 Percent"
url: https://www.infoq.com/articles/adaptive-hedged-requests-p99-latency/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-28T09:00:00+00:00
fetched_at: 2026-05-29T00:08:21.832677+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Fan-out 微服務架構中，慢速請求在跨多服務累積時，導致 p99 延遲遠高於各服務個別指標。提出適應性對沖機制（adaptive hedging）結合三層技術：DDSketch 進行實時分位數估計、windowed rotation 處理分佈漂移、token-bucket 預算防止負載放大。實測 p99 延遲降低 74%。"
key_points:
  - "DDSketch + windowed rotation + token-bucket 三層組合優化 p99 延遲 74%"
  - "解決 stragglers 在 fan-out 架構中的延遲積累問題"
  - "token-bucket 預算機制防止對沖導致的負載倍增"
tags: [p99-latency, hedged-requests, ddsketch, microservices, performance]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: Stragglers, Not Failures: How Adaptive Hedged Requests Reduce p99 Latency by 74 Percent

Fan-out 微服務架構中，慢速請求在跨多服務累積時，導致 p99 延遲遠高於各服務個別指標。提出適應性對沖機制（adaptive hedging）結合三層技術：DDSketch 進行實時分位數估計、windowed rotation 處理分佈漂移、token-bucket 預算防止負載放大。實測 p99 延遲降低 74%。

### 重點
- DDSketch + windowed rotation + token-bucket 三層組合優化 p99 延遲 74%
- 解決 stragglers 在 fan-out 架構中的延遲積累問題
- token-bucket 預算機制防止對沖導致的負載倍增

**原文：** [infoq-main](https://www.infoq.com/articles/adaptive-hedged-requests-p99-latency/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

n fan-out microservice architectures, slow-but-completing requests accumulate across services and drive p99 latency far higher than per-service metrics suggest. This article presents an adaptive hedging mechanism that uses DDSketch for real-time quantile estimation, windowed rotation to handle distribution drift, and a token-bucket budget to prevent load amplification. By Prathamesh Bhope

</details>