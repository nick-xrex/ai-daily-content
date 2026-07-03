---
id: inbox_2e302ee0
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/presentations/service-level-prioritized-load-shedding/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Anirudh Mendiratta, Benjamin Fedorka"
published_at: 2026-07-02T09:20:00+00:00
fetched_at: 2026-07-02T22:00:39.016137+00:00
content_hash: "046583f4113afd6b09d98b51c678d3430d0a808592c74dce55bf806523185ef6"
lang: en
caption_quality: None
raw: true
topics: []
---

# Presentation: Enhancing Reliability Using Service-Level Prioritized Load Shedding at Netflix

The speakers discuss Netflix’s architecture for surviving extreme traffic spikes. They explain the mechanics of prioritized load shedding embedded in their Envoy sidecar proxy, allowing user-initiated requests to steal capacity from non-critical traffic. They share automated platform strategies for continuous chaos load testing, config generation, and retry storm mitigation. By Anirudh Mendiratta, Benjamin Fedorka