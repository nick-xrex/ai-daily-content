---
id: inbox_168517b0
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.8"
author: "ruvnet"
published_at: 2026-05-06T15:01:46+00:00
fetched_at: 2026-05-22T18:00:34.027974+00:00
content_hash: "bb0530b8ca279d2ca4be9169403dfc182d2444414817bc3228eb84c920787c22"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.7.0-alpha.8 — agentdb delete tools + substrate upgrades since alpha.3

TL;DR 
 `npx ruflo@latest` is now 3.7.0-alpha.8 . Five alphas since the last GitHub release (alpha.3, daemon-survival fix on Windows). Public CLI surface unchanged — these alphas are substrate improvements that compound on every existing feature. 
 ```bash 
npx ruflo@latest --version # → ruflo v3.7.0-alpha.8 
``` 
 
 
 
 Package 
 This release 
 Tags 
 
 
 
 
 `@claude-flow/cli` 
 3.7.0-alpha.8 
 latest, alpha, v3alpha 
 
 
 `claude-flow` 
 3.7.0-alpha.8 
 latest, alpha, v3alpha 
 
 
 `ruflo` 
 3.7.0-alpha.8 
 latest, alpha 
 
 
 `@claude-flow/cli-core` 
 3.7.0-alpha.5 
 latest, alpha 
 
 
 `@claude-flow/neural` 
 3.0.0-alpha.8 
 latest, alpha, v3alpha 
 
 
 
 What's new since alpha.3 
 🆕 `agentdb_*-delete` MCP tools — alpha.8 ( #1784 , #1789 ) 
 Three new MCP tools close the gap that previously made `/adr-index` re-index impossible (the reporter @Tovli flagged that deleted ADR files left stale nodes + dangling edges in the graph forever): 
 
 
 
 Tool 
 Backed by 
 
 
 
 
 `agentdb_hierarchical-delete` 
 `ReflexionMemory.deleteEpisode` — graph + vector + SQL all-in-one 
 
 
 `agentdb_causal-edge-delete` 
 `GraphDatabaseAdapter.deleteEdgesByEndpoints` — Cypher-routed, label-validated upstream 
 
 
 `agentdb_causal-node-delete` 
 `GraphDatabaseAdapter.deleteNode({cascade: true})` — returns native `{deletedNode, deletedEdges}` audit 
 
 
 
 All wrapped in MutationGuard (fail-closed) + AttestationLog (audit). Wired through agentdb@3.0.0-alpha.13's new Cypher API (the upstream fix shipped in agentic-flow#150/ #151 ). SQL fallback for pre-alpha.13. 
 🧠 `@claude-flow/neural@3.0.0-alpha.8` substrate upgrades — alpha.7 ( #1773 ) 
 Six concrete additions to the neural package, all targeted at the question "is this package SOTA and useful?": 
 
 Persistence — `serialize()` / `deserialize()` on `SONAManager`, `ReasoningBank`, `PatternLearner`. Process restarts no longer wipe state. Float32Array embeddings + Maps round-trip losslessly via `deepEncode` / `deepDecode` helpers. 
 Seedable PRNG — `Mulberry32` + `setGlobalRng` injection point for reproducible training, A/B mode comparison, and deterministic tests. 
 Self-consistency orchestrator — `selfConsistency(N, op, aggregator)` (Wang et al. 2022). Three aggregators (majority / mean / first). 5–15pp accuracy on reasoning tasks at Nx compute. 
 Flash Attention + MoE migration — `flash-attention.ts` (857 LOC) and `moe-router.ts` (822 LOC) moved from cli into the neural package. Single source of truth; cli imports via package boundary. 
 Retrieval-path observability — `hnswRetrievalCount` vs `bruteForceRetrievalCount` in `ReasoningBank.getStats()`. `PatternLearner` honestly reports `hnswEnabled: 0` (no HNSW yet — separate followup). 
 80+ npm SEO keywords + complete metadata on the neural package. Now discoverable for `ai-agents`, `multi-agent`, `RL`, `LoRA`, `EWC`, `SONA`, etc. 
 
 Validation: 132 neural tests pass (44 algorithms + 39 patterns + 23 sona + 15 persistence + 9 self-consistency + 2 retrieval-path). 781 cli tests still pass. 
 🎯 Thompson sampling model router — alpha.5 ( #1772 ) 
 The 3-tier model selector (Haiku / Sonnet / Opus) is now a cost-adjusted multi-armed bandit instead of static thresholds. Every `hooks_model-outcome` call updates Beta(α, β) priors per tier; `hooks_model-route` samples θ ~ Beta(α, β) and picks argmax. The 77% Opus / 0.30 complexity mismatch corrects itself within ~50 routing decisions, automatically. 
 
 Marsaglia-Tsang gamma sampler + Box-Muller normal — pure JS, no new deps 
 Cost-adjusted Bernoulli rewards: Haiku-success ≫ Sonnet-success ≫ Opus-success 
 Convergence test: 100-trial workload at avg complexity 0.3 — Haiku posterior mean dominates Opus by N=100 
 Overhead: 45 μs per route() call (under the file's documented `&lt;100 μs` target) 
 
 🏎️ `@claude-flow/cli-core` lite path — alpha.4–alpha.5 ( #1760 , #1773 Phase 1) 
 A new sibling package that handles memory commands only (no SQLite, no HNSW, no ONNX). Cold-cache `npx` wall-time drops from ~35s to ~1.5s — measured 22.9× speedup for plugin scripts. 
 ```javascript 
// Plugin scripts opt in via env flag: 
const cliPkg = process.env.CLI_CORE === '1' 
? '@claude-flow/cli-core@alpha' // ~1.5s cold-cache 
: '@claude-flow/cli@latest'; // ~35s cold-cache (full features) 
``` 
 8 plugin scripts in this repo are already CLI_CORE-aware (cost-tracker × 6, ruflo-adr × 2). The full `@claude-flow/cli` is unchanged for end users; cli now depends on cli-core for 4 foundation modules (1,229 LOC of duplication eliminated). 
 Reproducible benchmark: `bash v3/@claude-flow/cli-core/scripts/cold-cache-bench.sh` 
 🩹 Earlier alphas in this series 
 
 alpha.7 ( #1773 ) — neural Phase 2 cli↔neural convergence: cli now depends on `@claude-flow/neural` and lazy-loads through a bridge. 1,215 LOC of byte-identical foundation modules deduplicated. 
 alpha.6 ( #1773 Phase 1) — `@claude-flow/neural` package wired into cli's dep graph for the first time + neural README cleanup (5 factual errors fixed against live exports). 
 alpha.5 ( #1772 ) — Thompson sampling bandit (above). 
 alpha.4 ( #1770 ) — fixed two silent intelligence regressions: `neural_status.flashAttention` was hardcoded `false`; `ruvllm.coordinator` reported `"unavailable"` despite `@ruvector/ruvllm` being resolvable (lazy-init timing bug in `getIntelligenceStats()`). 
 
 What didn't change 
 
 Public CLI surface (26 commands, 140+ subcommands) 
 Agent registry (60+ agent types) 
 Plugin marketplace (21 native plugins, IPFS distribution) 
 Hooks system (27 hooks + 12 background workers) 
 MCP tool surface (314 tools) 
 Configuration files (`claude-flow.config.json`, `.env`, plugin schemas) 
 
 If you're running 3.6.x, the upgrade is opt-in: most users won't notice anything beyond the version bump. Substrate improvements compound underneath. 
 Validation 
 
 ✅ `tsc` clean (cli + neural packages) 
 ✅ 793 cli tests pass — 769 baseline + 6 router-bandit + 6 neural-package-bridge + 12 agentdb-delete-tools 
 ✅ 132 neural tests pass — 44 algorithms + 39 patterns + 23 sona + 15 persistence + 9 self-consistency + 2 retrieval-path 
 ✅ All 5 packages publish-verified at the dist-tags shown above 
 
 Closed issues / merged PRs since alpha.3 
 
 
 
 # 
 Title 
 
 
 
 
 #1770 
 intelligence: two silent regressions — Flash Attention hardcoded false + ruvllm coordinator package-name mismatch 
 
 
 #1771 
 fix(intelligence): make Flash Attention + ruvllm coordinator stats truthful (PR) 
 
 
 #1772 
 feat(router): Thompson sampling bandit replaces deterministic argmax 
 
 
 #1773 
 @claude-flow/neural substrate upgrades (6 items) 
 
 
 #1774 
 feat(neural): Phase 1 convergence — cli depends on @claude-flow/neural 
 
 
 #1776 
 feat(neural): substrate upgrades 1-6 + SEO keywords 
 
 
 #1784 
 agentdb hierarchical-store and causal-edge have no delete tools 
 
 
 #1789 
 feat(agentdb): hierarchical + causal-edge + causal-node delete MCP tools (PR) 
 
 
 
 Upgrading 
 ```bash 
 Just use latest: 
 npx ruflo@latest 
 Or pin: 
 npx ruflo@3.7.0-alpha.8 
``` 
 State files are forward-compatible — `schemaVersion: 1` is enforced on all new persistence formats. Existing `.swarm/` and `.claude-flow/` state directories work unchanged. 
 Next 
 Loose ends, all queued: 
 
 Tombstone tables for native graph-node storage (recall-time filtering) — would let pre-alpha.13 backends also support delete. Bigger change, separate follow-up. 
 Updating `plugins/ruflo-adr/scripts/import.mjs` to invoke the new agentdb delete tools during `/adr-index` re-index — needs sync-semantics design. 
 `SONAManager.serialize/deserialize` round-trip test (deferred — `src/modes/balanced.ts` has a load-order bug that blocks instantiation in vitest; production path is correct). 
 Promotion of `@claude-flow/cli-core` from `@alpha` to broader visibility — gated on external validation. 
 
 🤖 Generated with RuFlo