---
id: inbox_c2ae491d
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/08/cloudflare-meerkat-consensus/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Renato Losio"
published_at: 2026-08-02T06:17:00+00:00
fetched_at: 2026-08-02T22:12:42.638169+00:00
content_hash: "a7ea8ef089b6405338fcdcf2ac0f27c4991b163185bdaa134ce30add37cf8a2e"
lang: en
caption_quality: None
raw: true
topics: []
---

# Cloudflare Introduces Meerkat for Strongly Consistent Global Coordination

Cloudflare recently introduced Meerkat, an internal globally consistent control-plane service based on the QuePaxa consensus algorithm. Unlike Raft, it allows leaderless writes while preserving strong consistency, improving availability across Cloudflare's global network. By Renato Losio