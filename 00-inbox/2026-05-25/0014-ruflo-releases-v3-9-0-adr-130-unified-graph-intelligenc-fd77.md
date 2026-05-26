---
id: inbox_bd9f7cfa
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.9.0"
author: "ruvnet"
published_at: 2026-05-25T03:05:56+00:00
fetched_at: 2026-05-26T00:14:49.535789+00:00
content_hash: "fd775eb83155812064a4019e4f0f2e803189f9796482d41b4bab216c50ada9ac"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.9.0 — ADR-130 Unified Graph Intelligence Backend

ADR-130 — Unified Knowledge Graph Backend (All 6 Phases) 
 Gives all 4 existing graph layers ( graph-node , AgentDB , ruflo-knowledge-graph , ruflo-graph-intelligence ) a shared graph_edges sql.js table with PQ-encoded embeddings, two new MCP tools, SONA trajectory hooks, and a plugin adapter contract. 
 New features 
 Phase 1 — graph_edges schema + PQ encoder 
 
 graph_edges table with temporal columns: confidence , decay_rate , last_reinforced , witness_id , embedding_ref 
 embedding-quantization.ts : Int8 global-scalar PQ (400 bytes/384-dim); inlineCosine() for zero-decode similarity 
 graph-edge-writer.ts : thin sql.js accessor with fire-and-forget writes 
 
 Phase 2 — agentdb_graph-query MCP tool 
 
 k-hop traversal via recursive CTE (sql-cte backend) 
 Personalized PageRank (PPR) power iteration 
 Semantic cosine ranking on inline PQ embeddings 
 complexityBudget enforcement: maxNodesVisited , maxDepth , maxMillis 
 
 Phase 3 — SONA trajectory-to-graph hooks 
 
 hooks_intelligence_trajectory-step : writes trajectory-caused edges fire-and-forget 
 hooks_post-task (success=true): writes reinforced-by edges fire-and-forget 
 Neither write blocks tool response (&lt;200ms latency preserved) 
 
 Phase 4 — Plugin adapter contract 
 
 GraphEdgesSource class: default KnowledgeGraphSource reading from graph_edges 
 createAutoGraphAdapter() : zero-boilerplate autoRegister path 
 graph_adapter field in plugin.json schema (documented in ruflo-plugin-creator SKILL.md) 
 
 Phase 5 — agentdb_graph-pathfinder MCP tool 
 
 6 algorithm variants: personalized-pagerank , dynamic-mincut , spectral-sparsify , temporal-centrality , connected-component-churn , witness-chain-divergence 
 Depth &gt; 5 clamped; non-existent seed returns empty paths not error 
 
 Phase 6 — Benchmark + CI 
 
 benchmark-graph.mjs : 6/6 targets met (2345 ops/sec write, 578 bytes/edge, k-hop depth=1 p99=4.9ms) 
 5 new CI jobs in v3-ci.yml gating all phases 
 
 Benchmark 
 
 
 
 Metric 
 Result 
 Target 
 
 
 
 
 Write throughput 
 2345 ops/sec 
 ≥500 ✓ 
 
 
 SQLite footprint 
 578 bytes/edge 
 ≤1024 ✓ 
 
 
 k-hop depth=1 p99 
 4.9ms 
 &lt;10ms ✓ 
 
 
 k-hop depth=3 p99 
 0.1ms 
 &lt;50ms ✓ 
 
 
 PQ encode p99 
 0.063ms 
 &lt;1ms ✓ 
 
 
 PQ decode p99 
 0.031ms 
 &lt;0.5ms ✓ 
 
 
 
 Test baseline 
 1999 passed | 46 skipped — no regression 
 PR: #2129 | Tracking: #2128