---
id: inbox_04a8b950
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/05/openai-voice-ai-scale/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Eran Stiller"
published_at: 2026-05-20T12:30:00+00:00
fetched_at: 2026-05-21T09:17:36.016357+00:00
content_hash: "0fbd6e2ff1cc9c62a2d787ff28dc12330da5f0a5046dac40c804dd687dbac1e3"
lang: en
caption_quality: None
raw: true
topics: []
---

# OpenAI Outlines WebRTC Architecture for Low-Latency Voice AI at Scale

OpenAI recently outlined how it adapted WebRTC for low-latency voice AI at global scale. The new architecture replaced a conventional media termination model with a relay-transceiver design better suited to Kubernetes and cloud load balancers. It keeps WebRTC session state in a dedicated transceiver layer while using relays to reduce public UDP exposure and keep media routing close to users. By Eran Stiller