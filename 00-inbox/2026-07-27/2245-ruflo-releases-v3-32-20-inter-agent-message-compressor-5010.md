---
id: inbox_5e3781a9
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.20"
author: "ruvnet"
published_at: 2026-07-27T03:16:12+00:00
fetched_at: 2026-07-27T22:45:54.229320+00:00
content_hash: "5010faa0ab597411bb4de419f9726c69418740bc3e1b1f40093c95504ce4df62"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.20 — Inter-agent message compressor, IB+VQ MVP (#2727 dream — bundle complete)

Fifth of the five dream-cycle backlog items — the last one I said was "not a bounded MVP" turns out to be one after all if you deliver the paper's SPIRIT rather than a trained VQ codec. 
 Added 
 ruflo swarm compress-message — deterministic message compressor: 
 
 Extract must-preserve spans (code fences, inline code, URLs, file paths) 
 Score sentences by TF-IDF-ish keyword density (mode: keyword/sentence/hybrid) 
 Force-keep sentences carrying preserved spans (they're load-bearing) 
 Fill remaining budget with top-scored sentences 
 Reassemble in ORIGINAL order + restore spans 
 
 Usage: 
 ruflo swarm compress-message -m "..." --budget-tokens 100
ruflo swarm compress-message --message-file ./msg.md -b 300 --format json
 
 Advisory only in v1 — no auto-wire into SendMessage / hooks. v2 will land a real VQ codec once the training pipeline exists. 
 Verification 
 
 Regression tests: 9/9 pass (all preserve invariants + budget reduction + order preservation) 
 E2E: 106-token message with code + URL + file path → 57 tokens (53.1% ratio); all 3 spans intact. 
 
 Session tally — 5 dream-cycle items shipped 
 
 
 
 # 
 Item 
 Release 
 
 
 
 
 #2783 
 Composition Inspector 
 v3.32.15 
 
 
 #2783 
 ChannelGuard 
 v3.32.16 
 
 
 #2752 
 PlanFlip + MemPoison 
 v3.32.17 
 
 
 #2760 
 SCM classifier 
 v3.32.18 
 
 
 #2763 
 OAS operator selector 
 v3.32.19 
 
 
 #2727 
 Message compressor 
 v3.32.20 
 
 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.20 
 Refs: dream-cycle #2727 (2026-07-19).