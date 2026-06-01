---
id: inbox_cb58e678
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/06/aws-api-gateway-auth-bypass/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Steef-Jan Wiggers"
published_at: 2026-06-01T09:55:00+00:00
fetched_at: 2026-06-01T22:46:05.041148+00:00
content_hash: "cb5a1bc371b5291e5a174bdfb17048cfc521c82b406e5c8fcfa9303b06c26bce"
lang: en
caption_quality: None
raw: true
topics: []
---

# A Trailing Slash Bypassed AWS API Gateway Authorization

A security researcher found that adding a trailing slash to AWS HTTP API paths bypassed Lambda authorizer authentication entirely, enabling unauthenticated wire transfers at a fintech. The root cause is a path normalization mismatch between HTTP API's greedy route matching and its authorization layer. The same vulnerability class appeared in gRPC-Go via CVE-2026-33186. By Steef-Jan Wiggers