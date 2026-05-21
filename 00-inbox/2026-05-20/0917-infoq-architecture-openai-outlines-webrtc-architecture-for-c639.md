---
id: inbox_ed79be5e
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/05/openai-voice-ai-scale/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Eran Stiller"
published_at: 2026-05-20T12:30:00+00:00
fetched_at: 2026-05-21T09:17:37.822000+00:00
content_hash: "c639b76cba4f246de10c18befc6ee1a977ea15f29e51f7e4f5d5b87f99b152f5"
lang: en
caption_quality: None
raw: true
topics: []
---

# OpenAI Outlines WebRTC Architecture for Low-Latency Voice AI at Scale

OpenAI recently outlined how it adapted WebRTC for low-latency voice AI at global scale. The new architecture replaced a conventional media termination model with a relay-transceiver design better suited to Kubernetes and cloud load balancers. It keeps WebRTC session state in a dedicated transceiver layer while using relays to reduce public UDP exposure and keep media routing close to users. By Eran Stiller