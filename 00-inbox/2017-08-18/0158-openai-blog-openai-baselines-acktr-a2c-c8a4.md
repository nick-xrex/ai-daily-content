---
id: inbox_5e4e242b
source: openai-blog
source_type: rss
url: "https://openai.com/index/openai-baselines-acktr-a2c"
author: ""
published_at: 2017-08-18T07:00:00+00:00
fetched_at: 2026-04-21T01:58:18.564331+00:00
content_hash: "c8a482ed85b172afd515053910f48f354382315bcb28e2a435f0ffb1ead2711b"
lang: en
caption_quality: None
raw: true
topics: []
---

# OpenAI Baselines: ACKTR & A2C

We’re releasing two new OpenAI Baselines implementations: ACKTR and A2C. A2C is a synchronous, deterministic variant of Asynchronous Advantage Actor Critic (A3C) which we’ve found gives equal performance. ACKTR is a more sample-efficient reinforcement learning algorithm than TRPO and A2C, and requires only slightly more computation than A2C per update.