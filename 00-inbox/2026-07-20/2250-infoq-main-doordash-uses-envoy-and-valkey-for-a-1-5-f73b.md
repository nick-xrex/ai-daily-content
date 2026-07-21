---
id: inbox_4975bbd4
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/07/doordash-entity-cache-proxy/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Leela Kumili"
published_at: 2026-07-20T13:53:00+00:00
fetched_at: 2026-07-20T22:50:38.792559+00:00
content_hash: "f73b6ff04dbb3fadcf1bc6f49d8c28ae54a530e5c41e9db2fe9ae760b5a9fba8"
lang: en
caption_quality: None
raw: true
topics: []
---

# DoorDash Uses Envoy and Valkey for a 1.5M RPS Proxy Cache with 99.99999% Availability

DoorDash has developed Entity Cache, a transparent proxy caching platform built on Envoy and Valkey to reduce redundant service-to-service requests across its microservices architecture. Operating within DoorDash’s service mesh, the platform serves over 1.5M requests per second with 99.99999% availability through caching, event-driven invalidation, failure handling, and performance optimizations. By Leela Kumili