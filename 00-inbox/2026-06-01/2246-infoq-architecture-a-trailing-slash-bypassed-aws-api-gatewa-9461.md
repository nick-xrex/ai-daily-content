---
id: inbox_d0361920
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/06/aws-api-gateway-auth-bypass/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Steef-Jan Wiggers"
published_at: 2026-06-01T09:55:00+00:00
fetched_at: 2026-06-01T22:46:06.452174+00:00
content_hash: "946165b82a72198a73c14d069a3f3577ce39cf39c7f1bed3e8c62080a38264b1"
lang: en
caption_quality: None
raw: true
topics: []
---

# A Trailing Slash Bypassed AWS API Gateway Authorization

A security researcher found that adding a trailing slash to AWS HTTP API paths bypassed Lambda authorizer authentication entirely, enabling unauthenticated wire transfers at a fintech. The root cause is a path normalization mismatch between HTTP API's greedy route matching and its authorization layer. The same vulnerability class appeared in gRPC-Go via CVE-2026-33186. By Steef-Jan Wiggers