---
id: inbox_17e564c9
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.13"
author: "ruvnet"
published_at: 2026-05-30T00:15:31+00:00
fetched_at: 2026-05-30T02:16:29.842007+00:00
content_hash: "9af90a09a49b2f72a19e5428b95e426e2d0c81decbdd83c3e696ad43eb077040"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.13 — agentdb ADR-073 SOTA round

Bumps the bundled agentdb to 3.0.0-alpha.16 ( ruvnet/agentdb#6 — SOTA roadmap, ADR-073). Three categories of improvement: 
 Security — three findings closed: 
 
 parseJsonStrict helper applied to the unguarded JSON.parse site (no more SyntaxError / stack-trace leak from crafted CLI input) 
 validateSqlIdentifier on the residual CWE-89 template-SQL in migrate.ts 
 crypto.randomBytes() IDs in agentdb-fast + GraphDatabaseAdapter (CWE-338) 
 
 MCP surface (3 new tools) : 
 
 causal_traverse — multi-hop graph walk for "why does this memory matter?" 
 agentdb_delete_batch — atomic IN-clause delete with id + table whitelist 
 consolidate_now — on-demand NightlyLearner run instead of waiting for a scheduled pass 
 
 Honest measurement : 
 
 Real recall@k benchmark harness committed ( scripts/benchmark-recall.mjs ) 
 Production-dim run at N=2000 D=384 measures recall@10 = 0.912 (above the documented 0.90 CI floor; the prior "95%" claim was unverified — committed run JSON replaces it) 
 CI guard in tests/recall-benchmark-harness.test.ts fails if recall drops below 0.90 
 
 Tests: 14 new regression tests across security + MCP-handler building blocks + recall floor. 
Full ruflo CLI suite still 2104/0/46-skipped. 
 Install: npx ruflo@3.10.13 
 Bigger SOTA items (RaBitQ 1-bit quantization, worker-thread batch pool, async HNSW rebuild, learned reranking head, tier-aware memory + EWC wiring) are tracked in ruvnet/agentdb#6 for the next round.