---
id: inbox_8027f38a
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.13"
author: "ruvnet"
published_at: 2026-07-27T00:32:51+00:00
fetched_at: 2026-07-27T01:23:04.170458+00:00
content_hash: "c336d85e2c46bb647438d0903f8fb7e2a9fd1ba79bca8946d19fad37e78607e8"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.13 — Mixture-of-Agents route mode (#2778 dream)

Closes the last item of the 2026-07-26 dream-cycle 3-task bundle. 
 Added 
 hooks route --mode moa — Mixture-of-Agents fanout plan. Dream-cycle #2778 (arXiv 2605.01566, ACL 2026 SRW): test-time scaling is Pareto-optimal when parallel generations exceed sequential aggregations — +2.7pp accuracy over self-consistency at equal cost. 
 New flags: 
 
 --mode single|moa (default: single) — opts into MoA planning. 
 --moa-parallel N (default: 3) — fanout width. Distinct name to avoid a boolean-flag collision with --parallel in swarm/workflow. 
 --consensus majority-vote|best-confidence (default: majority-vote). 
 
 When --mode=moa , the router adds a moaPlan field to the result telling the caller to spawn N parallel Haiku Task calls with the primary agent's role, then a synthesizer Task that reads all N verdicts and picks the majority (or highest-confidence) answer. The rationale field explains whether the swap saves cost (only unambiguously below Tier-3 Sonnet). 
 E2E verified: hooks route --mode moa --moa-parallel 7 → 7 Haiku agent slots + 1 synthesizer, JSON output splices moaPlan cleanly, single mode omits the plan. 
 Upgrade 
 npx ruflo@latest --version # → 3.32.13 
 Refs: dream-cycle #2778 .