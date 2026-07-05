---
id: inbox_0acce01e
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.21.0"
author: "ruvnet"
published_at: 2026-07-04T13:19:25+00:00
fetched_at: 2026-07-04T22:00:22.958167+00:00
content_hash: "1139ed533f78ac71abcae1b9baa0a4e079296599b3bbf218eaf129ea3dea8014"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.21.0 — agenticow governed learning loop (branch · test · judge · promote · rollback)

Turns agent execution into a governed learning loop with provenance on every decision. 
 New 
 
 agenticow COW memory substrate (ADR-170) — 9 MCP verbs (branch/checkpoint/rollback/promote + ingest/query/diff/lineage/status), 162-byte branches, nativeAnn Rust fast-path, one shared loader 
 Per-agent COW branches (opt-in), speculative branch-and-promote ( agenticow_speculate ), checkpoint/rollback gate for autopilot loops 
 Provenance-tiered evaluation oracle (ADR-171) — execution-oracle → Fable judge → structural proxy, each label tagged resolvedBy ; promote-gate (proxy can NEVER clear); causal failure receipts 
 Fable advisor harness (ADR-172) — cost-disciplined claude -p (clean-cwd + batching = $1.56→~$0.02/item); judge + GEPA reflector 
 weight-eft $0 distill slice + remote-GPU train (ADR-173) — export/plan/eval + neural distill train --remote (OFFLINE dry-run default, --execute --yes gated, --preflight opt-in) 
 
 Safety (adversarial RC pass — all fail-closed) 
 Promote unresolved branch → ineligible · proxy-as-gold → can't clear · SSH without --execute --yes → offline/refused · Fable without opt-in → no call · rollback after partial write → restores. 
 Bundles: agenticow 0.2.4, @ruvector/ruvllm 2.6.0. ADR-150 optional-deps + graceful degradation throughout. Startup 0.12s. New CI lockfile-drift guard ( #2563 ). 
 PRs: #2562 · ADRs 170-173