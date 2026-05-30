---
id: inbox_95432e09
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.7"
author: "ruvnet"
published_at: 2026-05-29T16:16:56+00:00
fetched_at: 2026-05-30T02:16:29.846896+00:00
content_hash: "dc67abc0ea8bda8cc151efef2776b145c19a52e9289ae1b1be1cf4d8661d1bad"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.7 — intelligence audit, hardening fixes & honest perf numbers

Ruflo v3.10.7 — intelligence self-learning audit, hardening fixes &amp; honest performance numbers 
 A full empirical audit of the self-learning/intelligence system, the prioritized fixes it surfaced, and a rewrite of all performance claims to measured values. Audit + reusable benchmark harness included. 
 🔴 Critical fix — negative-reward inversion (follow-up to #2222 ) 
 route feedback -r -1.0 (and --reward -1.0 ) was parsed as +1.00 — the shared CLI flag parser dropped any - -prefixed value, so giving negative feedback actively reinforced the bad agent. Fixed in parser.ts (negative numeric literals are now accepted as flag values); all three syntaxes yield −1.0. Verified in the published artifact. 
 Other fixes 
 
 Removed a fabricated metric — Flash Attention "speedup" was reported from a runtime RNG in both attention-coordinator copies; now an honest "unmeasured" sentinel. 
 Embedding observability — generateEmbedding returns backend: onnx|mock , surfaced in memory_bridge_status / import so a mock (hash-fallback) embedding is never mislabeled as the real ONNX model. 
 MCP learning — trajectory-end no longer feeds EWC a synthetic gradient; hooks_intelligence_learn runs a real distill/consolidate cycle. 
 
 HNSW optimization (genuine, measured) 
 Root cause: HNSW was never actually running — the ruvector adapter passed no storagePath , the native DB's file lock was held by a daemon, and a silent catch{} degraded to brute force. Fixed (unique storagePath, hnswConfig {m:32, efConstruction:200} , visible fallback warning). Same-harness before→after: N=5000 0.92×→3.2–4.7×, N=20000 0.95×→1.89× (recall@10 0.88–0.99). 
 Honest performance numbers 
 README + CLAUDE.md perf tables now show measured values from the new scripts/benchmark-intelligence.mjs : 
 
 Int8 quantization 3.84× (reconstruction cosine 0.99999) · RaBitQ 32× memory · SONA adapt 0.0043 ms · MoE gate converges (0.13→0.88) 
 HNSW "150×–12,500×" and Flash "2.49–7.47×" marked NOT reproduced / unverified (no benchmark supports them) 
 
 Full audit: docs/reviews/intelligence-system-audit-2026-05-29.md . All three packages published at 3.10.7 ( latest / alpha / v3alpha in lockstep). 
 🤖 Generated with RuFlo