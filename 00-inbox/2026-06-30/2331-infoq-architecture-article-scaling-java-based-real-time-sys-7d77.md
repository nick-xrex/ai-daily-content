---
id: inbox_2e7efef7
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/articles/tradeoffs-event-driven-design/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Sagar Deepak Joshi"
published_at: 2026-06-30T09:00:00+00:00
fetched_at: 2026-07-01T23:31:42.083326+00:00
content_hash: "7d77cd29d393d6c839eb80913a7246f8c92063653b8caf63d404f0dcd8f85e05"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: Scaling Java-Based Real-Time Systems: The Hidden Tradeoffs of Event-Driven Design

Event-driven architecture promises scalability, but in Java-based real-time systems the tradeoffs only surface in production. Drawing on a Java/Kafka contact center platform handling 80k BHCC across 10k agents, this article details where the design breaks down—state management, partition limits, deduplication, JVM tuning, cascading consumer failures—and the Redis-backed patterns that fixed each. By Sagar Deepak Joshi