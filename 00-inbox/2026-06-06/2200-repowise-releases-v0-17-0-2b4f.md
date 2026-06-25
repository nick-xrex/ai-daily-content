---
id: inbox_323bc16d
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.17.0"
author: "github-actions[bot]"
published_at: 2026-06-06T14:32:01+00:00
fetched_at: 2026-06-25T22:00:26.066447+00:00
content_hash: "2b4f877321869bd9445766de424488afa6864b2394e9550c3f6b6076e8a5ea00"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.17.0

What's Changed 
 
 feat(plugin): Claude Code plugin + root marketplace, refreshed to current surface by @RaghavChamadiya in #356 
 fix(health): calibrate hotspot + ownership risk for small teams and quiet repos by @RaghavChamadiya in #363 
 fix(web): decode breadcrumb path labels by @joptimus in #359 
 fix(server): honor exclude_patterns in server jobs; prune stale rows by @joptimus in #354 
 fix(generation): close never-started page coroutines on Ctrl+C abort by @RaghavChamadiya in #365 
 feat(cli): owl mascot init banner with repo-seeded heatmap wordmark by @swati510 in #364 
 feat(git): agent-provenance layer in the git indexer by @RaghavChamadiya in #366 
 perf: make indexing &amp; incremental update scale with change size by @RaghavChamadiya in #368 
 perf: cache parsing and betweenness across incremental updates by @RaghavChamadiya in #369 
 feat: Distill - index-aware output distillation (distill / expand / saved) by @RaghavChamadiya in #378 
 feat(init): clearer mode panel + searchable model selection by @RaghavChamadiya in #379 
 fix(core): pruned filesystem walks — stop scanning nested repos and junk trees by @RaghavChamadiya in #380 
 fix: honor include-submodules across incremental updates and upgrades by @RaghavChamadiya in #381 
 fix(init): record the distill rewrite-hook verdict in every flow by @RaghavChamadiya in #382 
 perf(workspace): route already-indexed repos through the incremental update path by @RaghavChamadiya in #384 
 fix(ingestion): resolve explicit relative JS imports by @nkgotcode in #376 
 fix(analysis): honor persisted submodule flags in health and dead-code by @RaghavChamadiya in #383 
 fix: process hygiene - MCP orphan watchdog, live-PID update locks, PATH-hijack-proof registration by @RaghavChamadiya in #385 
 build(deps): bump starlette from 0.52.1 to 1.0.1 by @dependabot [bot] in #367 
 fix(health): use whole-file NLOC for health file metrics by @joptimus in #387 
 fix(ingestion): rescue local Express route middleware from unused-export detection by @joptimus in #386 
 fix(health): compute duplication_pct from the union of clone ranges by @RaghavChamadiya in #388 
 fix(distill): Grep-rescue correctness, PowerShell hook coverage, nudge floor, allowlist seeding by @RaghavChamadiya in #389 
 feat(distill): lint filter, missed-savings discovery, per-surface ledger tagging by @RaghavChamadiya in #390 
 feat(distill): Codex CLI rewrite support + repowise corrections by @RaghavChamadiya in #391 
 feat(ui,web): theme system, constellation graph, blueprint C4 canvas, web app adoption by @swati510 in #405 
 feat(tools): knowledge-graph validation harness with pinned 38-repo matrix by @swati510 in #404 
 fix(mcp): harden get_context — segment-boundary partial match, git-file fall-through, batch isolation by @swati510 in #401 
 feat(kg)!: multi-language resolution, curated knowledge-graph engine, curated wiki modules by default by @swati510 in #392 
 feat(distill): default the init rewrite-hook prompt to yes by @swati510 in #409 
 release: v0.17.0 — Distill, multi-language import resolution, light-default theme by @swati510 in #410 
 
 New Contributors 
 
 @nkgotcode made their first contribution in #376 
 
 Full Changelog : v0.16.0...v0.17.0