---
id: inbox_ff00cc14
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.71"
author: "ruvnet"
published_at: 2026-05-19T22:48:00+00:00
fetched_at: 2026-05-22T18:00:34.010037+00:00
content_hash: "4e73707a53d9a6302e5912cd73133b90ab86b231937cfa96cce50e5b0841d315"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.7.0-alpha.71 — ADR-125 Memory Consolidation (full delivery)

TL;DR — Delivers ADR-125 end-to-end. @claude-flow/memory now has a single canonical entry point, a real hybrid default (ADR-009 finally delivered), persistent HNSW that survives restart, a memory-bound consolidator, graceful retrieval degradation with FTS5 fallback, and reproducible benchmarks. All 8 ADR-125 acceptance criteria locked in. 
 
 Install / upgrade: 
 npx ruflo@latest # umbrella CLI 
npx claude-flow@latest # legacy umbrella 
npx @claude-flow/cli@latest 
 For direct memory-package consumers: 
 npm install @claude-flow/memory@latest 
 
 🧠 New: @claude-flow/memory@3.0.0-alpha.18 — full ADR-125 delivery 
 Delivered in two coordinated PRs: 
 
 PR A ( #2062 ) — Phases 1+2+6+7 — "deliver ADR-009" 
 PR B ( #2063 ) — Phases 3+4+5 — "harden" 
 
 What changed 
 
 
 
 Capability 
 What you can do now 
 
 
 
 
 Canonical entry point 
 import { MemoryService } from '@claude-flow/memory' . UnifiedMemoryService still works as a @deprecated alias. HnswLite and RvfBackend no longer pollute the top-level export. 
 
 
 Real hybrid default 
 createHybridService(config) returns a MemoryService backed by actual HybridBackend (sql.js + AgentDB). The apologetic AgentDB-only downgrade is gone. ADR-009 promise delivered. 
 
 
 Persistent HNSW 
 MemoryService.close() snapshots the HNSW index to a &lt;dbPath&gt;.hnsw sidecar (plus &lt;dbPath&gt;.meta.json for entries/namespaces/keys/tags). Reopening on the same path restores in milliseconds — no more O(n log n) rebuild on cold start. Auto-snapshots every Nth write. 
 
 
 MemoryConsolidator 
 New MemoryConsolidator service: sweepExpired() evicts past-TTL entries from indexes AND HNSW; dedup(strategy) content-hash-merges duplicates; compactHnsw() rebuilds the index after large churn. Auto-runs on a timer (default 6h). The nightlyLearner AgentDB controller now delegates here. 
 
 
 Graceful retrieval 
 service.search('foo') no longer throws when @claude-flow/embeddings is unavailable — it degrades to FTS5 keyword and emits health.embedder = 'degraded' . The full hybrid path ( hybridSearch controller) does real Reciprocal Rank Fusion (k=60) + MMR diversity rerank (λ=0.7). 
 
 
 Runnable benchmarks 
 npm run bench now actually runs. Five benchmark files (HNSW search/indexing, cache hit rate, memory write, vector search) + a committed baseline at benchmarks/results/baseline-20260519T212453Z.md . The README's 150x–12,500x perf claims are no longer aspirational prose. 
 
 
 RuVector boundary cleanup 
 Stray ruvector.db / *.redb / *.rvf artifacts get wiped automatically by vitest.setup.ts , gitignored, and locked in place by a new CI smoke ( scripts/smoke-memory-no-stray-db.mjs ) that fails if any reappear after npm test . 
 
 
 
 Acceptance criteria — all 8 ✅ 
 
 
 
 # 
 Criterion 
 Phase 
 Where 
 
 
 
 
 1 
 Top-level export lists MemoryService but NOT HnswLite / DDD / RvfBackend 
 1 
 PR A 
 
 
 2 
 createHybridService returns a service whose backend is instanceof HybridBackend 
 2 
 PR A 
 
 
 3 
 Restarting on same dbPath recovers entries AND HNSW (no rebuild log) 
 3 
 PR B 
 
 
 4 
 After 1000 expired entries, sweepExpired() empties entries AND HNSW 
 4 
 PR B 
 
 
 5 
 With embeddingGenerator: undefined , search('foo') returns FTS-ranked results (no throw) 
 5 
 PR B 
 
 
 6 
 npm run bench produces results files 
 6 
 PR A 
 
 
 7 
 git status after npm test is empty 
 7 
 PR A 
 
 
 8 
 Test files ≥14 after Phases 1–5 
 1–5 
 ✅ 15 files / 403 tests 
 
 
 
 Test count delta 
 pre-ADR-125: 367 tests / 10 files
post PR A: 378 tests / 11 files (+11 / +1)
post PR B: 403 tests / 15 files (+25 / +4)
TOTAL: +36 tests, +5 test files
 
 Backward compatibility 
 
 UnifiedMemoryService remains exported as a @deprecated alias to MemoryService through 3.0.0-rc . No breaking change. 
 HnswLite removed from public surface and its module deleted — verified zero external importers across the monorepo. Internal usage by RvfBackend inlined as a private helper. 
 RvfBackend removed from public exports (kept as internal). 
 semanticSearch no longer throws when embedder unavailable — behavior change for callers that depended on the throw to detect misconfigured embedders. New health.embedder = 'degraded' event surfaces the same signal. 
 
 
 📦 Published packages (npm) 
 
 
 
 Package 
 Version 
 Tags 
 
 
 
 
 @claude-flow/cli 
 3.7.0-alpha.71 
 alpha , latest , v3alpha 
 
 
 claude-flow 
 3.7.0-alpha.71 
 alpha , latest , v3alpha 
 
 
 ruflo 
 3.7.0-alpha.71 
 alpha , latest , v3alpha 
 
 
 @claude-flow/memory 
 3.0.0-alpha.18 
 alpha , latest , v3alpha 
 
 
 
 📜 PRs merged since alpha.70 
 
 #2063 — ADR-125 PR B — persistent HNSW + MemoryConsolidator + FTS5 fallback 
 #2062 — ADR-125 PR A — canonical MemoryService + real hybrid default + runnable benches 
 
 🔮 Deferred to follow-up ADRs (each gets its own decision record) 
 
 ADR-126 Provenance + causal edges ( MemoryEntry.source / signedBy , edge types caused-by | supersedes | derived-from ) 
 ADR-127 PII scan + AIDefence write-interceptor 
 ADR-128 Multi-tenant row-level isolation + encryption at rest 
 ADR-129 Real-time fs.watch + 3-way merge for AutoMemoryBridge 
 ADR-130 Event-sourced memory replay (extends ADR-007) 
 
 
 Full diff : v3.7.0-alpha.70...v3.7.0-alpha.71 
 Tracking issue : #2061 (closed)