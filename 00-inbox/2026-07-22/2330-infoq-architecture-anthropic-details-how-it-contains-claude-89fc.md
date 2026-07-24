---
id: inbox_4d3150bc
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/07/anthropic-claude-containment/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Eran Stiller"
published_at: 2026-07-22T12:25:00+00:00
fetched_at: 2026-07-22T23:30:42.988658+00:00
content_hash: "89fc218b8a108d3fe6d134f03ad9a8803f7541aba3d5c3077617c5fda91f47f1"
lang: en
caption_quality: None
raw: true
topics: []
---

# Anthropic Details How It Contains Claude Across Web, Code, and Cowork

Anthropic detailed the containment architectures it uses for Claude across its products. It argues that agent safety depends on placing deterministic limits on an agent’s filesystem, network, and execution environment rather than on permission prompts or safeguards. Most notably, it examines failures at trust boundaries and along permitted egress paths that led Anthropic to revise those designs. By Eran Stiller