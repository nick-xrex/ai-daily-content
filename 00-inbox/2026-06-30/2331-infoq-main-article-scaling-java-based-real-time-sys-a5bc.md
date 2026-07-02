---
id: inbox_682312e9
source: infoq-main
source_type: rss
url: "https://www.infoq.com/articles/tradeoffs-event-driven-design/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Sagar Deepak Joshi"
published_at: 2026-06-30T09:00:00+00:00
fetched_at: 2026-07-01T23:31:40.447035+00:00
content_hash: "a5bcec963791ff3ed51e55bfa42d15ad6d6dbb5ce75f3b608f08ef6d508b9391"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: Scaling Java-Based Real-Time Systems: The Hidden Tradeoffs of Event-Driven Design

Event-driven architecture promises scalability, but in Java-based real-time systems the tradeoffs only surface in production. Drawing on a Java/Kafka contact center platform handling 80k BHCC across 10k agents, this article details where the design breaks down—state management, partition limits, deduplication, JVM tuning, cascading consumer failures—and the Redis-backed patterns that fixed each. By Sagar Deepak Joshi