---
id: inbox_49f5221e
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/07/doordash-entity-cache-proxy/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Leela Kumili"
published_at: 2026-07-20T13:53:00+00:00
fetched_at: 2026-07-20T22:50:40.386256+00:00
content_hash: "775f7eca86ee17867bf051d1771f92155e91c3775cf2a2a91afcdd7d9311292f"
lang: en
caption_quality: None
raw: true
topics: []
---

# DoorDash Uses Envoy and Valkey for a 1.5M RPS Proxy Cache with 99.99999% Availability

DoorDash has developed Entity Cache, a transparent proxy caching platform built on Envoy and Valkey to reduce redundant service-to-service requests across its microservices architecture. Operating within DoorDash’s service mesh, the platform serves over 1.5M requests per second with 99.99999% availability through caching, event-driven invalidation, failure handling, and performance optimizations. By Leela Kumili