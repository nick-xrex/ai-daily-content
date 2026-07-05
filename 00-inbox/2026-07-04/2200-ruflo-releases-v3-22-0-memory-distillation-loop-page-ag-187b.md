---
id: inbox_44f9204f
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.22.0"
author: "ruvnet"
published_at: 2026-07-04T21:13:02+00:00
fetched_at: 2026-07-04T22:00:22.953631+00:00
content_hash: "187b2e0d4d9e16768dc86aa43da22dee414fe70cfc6b92b5cbebadff67204896"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.22.0 — memory distillation loop + page-agent intent + signed hook auto-refresh

Highlights 
 
 ADR-174 — Memory distillation self-learning loop. The daemon's consolidate worker was a stub writing zeros; it now really mines memory_entries → episodes → reasoning_patterns (+embeddings) → weak relational edges. $0 default, incremental, non-destructive, provenance-gated (ADR-171). memory distill run|status|config CLI + self-optimization ( distill-tuning ). Trains the local SONA/MoE model on your own memory. 
 Failure-signal capture. Hooks recorded a hardcoded success:true (898/898, 0 failures) — now they read Claude Code's PostToolUse outcome and record real failures, so the oracle tier finally has negative examples. 
 ADR-175 — page-agent browser intent. New browser_act MCP tool: natural-language intents on top of the selector tools. Strips page-agent's demo auto-connect to Alibaba's sandbox (fail-closed firewall) and proxies the LLM key so it never enters page context. 
 Version-stamped helper auto-refresh (secured). Hook fixes now propagate to every project on the next ruflo command — no re-init — gated by an Ed25519 signed manifest (key in GCP Secret Manager); a tampered helper is refused, not propagated. 
 
 Also: statusline vector-count + corruption auto-recovery ( #2569 ), memory-search recall ( #2558 ), agenticow/memory perf. 
 All backward-compatible additions. 3-package train ( @claude-flow/cli , claude-flow , ruflo ) at 3.22.0. 
 🤖 Generated with RuFlo