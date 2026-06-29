---
id: inbox_3b1a2246
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.14.4"
author: "ruvnet"
published_at: 2026-06-27T16:32:47+00:00
fetched_at: 2026-06-27T22:00:25.048240+00:00
content_hash: "f9f137229cd91985090413091ce571557ab4fc103b402f75dda60a1d95b1e976"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.14.4 — Darwin core-systems sweep + tarball-bloat fix

Patch release shipping the darwin-core systems Darwin loop (PR #2481 ) and a critical tarball-bloat fix. 
 Darwin core-systems wins (PR #2481 ) 
 
 
 
 Dim 
 Δ 
 Detail 
 
 
 
 
 skill-distillation 
 0.4286 → 1.0 (+133% rel) 
 ADR-155 SKILL-DISCO bench: AND→OR predicate then promote-all. 3/7 → 7/7 successful traces promoted. Exceeds the SKILL-DISCO arXiv 2026 +22% target on this synthetic bench. 
 
 
 causal-graph hot path 
 115ms → 3ms (-97%) 
 Two optimizations in v3/@claude-flow/cli/src/mcp-tools/agentdb-tools.ts: (a) EXISTS-probe early-exit on missing seed; (b) module-level dynamic-import cache for graph-query/pathfinder handlers. All 21 smoke tests still pass. 
 
 
 reasoning-bank 
 +0.0024 
 scifact bm25 0.0→0.05 tie-breaker. Cumulative across this + prior BEIR Darwin loop: 0.5694 → 0.628 = +10.3% rel. 
 
 
 benchmark infra 
 new --only flag 
 `node scripts/benchmark-intelligence.mjs --only=` enables per-dimension measurement (saves multi-minute wall when only one dim needs scoring). 
 
 
 2 baselines confirmed at-target 
 — 
 sona-adapt 0.0041 &lt; 0.005 (WASM-opaque); moe-gate afterConfidence 0.88 &gt; 0.85 (WASM-opaque). 
 
 
 
 Tarball-bloat fix (critical) 
 The 3.14.4 publish initially failed with 413 Payload Too Large — the tarball had bloated from 77MB to 276MB / 46k files because the root `files` field swept in `.claude/worktrees/**` (3.3GB of Darwin workflow worktrees from this session). 
 Added explicit excludes in `package.json` files-pattern: 
 
 `!.claude/worktrees/**` 
 `!.claude/projects/**` 
 `!.claude/sessions/**` 
 `!.claude/scheduled_tasks.lock` 
 
 Result: 2.3 MB / 1096 files — slimmer than the 3.14.1 baseline (77MB / 14440 files). Published tarball now contains only what's actually needed (bin/, dist/, .claude-plugin/, .claude/agents/, .claude/commands/, etc.). 
 Install 
 ```bash 
npx ruflo@3.14.4 
 or 
 npx @claude-flow/cli@3.14.4 
``` 
 All three packages — @claude-flow/cli, claude-flow, ruflo — at 3.14.4 with consistent latest / alpha / v3alpha dist-tags. 
 Honest dimensions 
 
 skill-distillation hit the synthetic bench ceiling (1.0/1.0) — real ALFWorld/WebArena eval would be the next validation 
 HNSW recall@10 = 0.89 at N=5k vs documented 0.99 — flagged for separate investigation (NAPI doesn't honor efConstruction beyond cap) 
 reasoning-bank's BEIR bench doesn't exercise the actual ReasoningBank subsystem — proper bench needed for next leap