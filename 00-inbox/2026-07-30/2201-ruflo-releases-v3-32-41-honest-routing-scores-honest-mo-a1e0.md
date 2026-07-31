---
id: inbox_e43d2bb9
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.41"
author: "ruvnet"
published_at: 2026-07-30T16:30:39+00:00
fetched_at: 2026-07-30T22:01:25.231717+00:00
content_hash: "a1e08987b5ea7b04cfb3ccadec2585658e69b8d8a27109af4a557181acce5fca"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.41 — honest routing scores, honest MoE metrics, real pattern transfer

Fixed 
 #2864 — hooks route gated learned routing patterns at score ≥0.65 vs static patterns at &gt;0.4, so a top-scoring learned pattern could lose to a lower-scoring static one that simply cleared the easier bar. Measured 49% agreement with the router's own recorded training labels on a real store (only 1/61 replayed routes decided by a learned pattern). Both sources now share the same score gate; support/reliability remain the learned-specific quality guard. 
 #2865 — the hooks intelligence MoE panel showed a hardcoded Routing Accuracy: 82.0% (plus Active Experts/Load Balance constants) whenever any local neural data existed, regardless of actual routing quality — the same "self-confidence presented as accuracy" problem already fixed on the hooks metrics path in an earlier release. These fields are now omitted rather than fabricated when no real value is reported. 
 #2859 — hooks transfer from-project reported success and quality stats (avgConfidence, avgAge) without ever reading or writing the destination project's memory store — every number was invented from fixed percentages of the source pattern count. Now performs a real merge: reads the destination, skips low-confidence/duplicate/conflicting entries, and actually persists whatever remains. Reported counts and stats are computed from what was actually processed. 
 All three verified against the exact reproductions in their issues using the real built CLI (not unit mocks). 
 PR: #2869 
 Packages 
 `@claude-flow/cli`, `claude-flow`, and `ruflo` are all at 3.32.41 ; `latest`, `alpha`, and `v3alpha` dist-tags all point to it.