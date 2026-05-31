---
id: inbox_4bfdd606
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.16"
author: "ruvnet"
published_at: 2026-05-30T16:33:20+00:00
fetched_at: 2026-05-30T18:00:42.586050+00:00
content_hash: "612137a2f2e402e0715c6b84d9077e46b5af9703b91a9ad6d7814faa58e22a8d"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.16 — Round B wiring + Round C Structured Distillation (ADR-076)

Two SOTA-direction rounds packaged together. 
 Round B — finishes the #2245 wiring story (closes the "wiring side" gap left in ADR-074/ADR-075) 
 
 hooks_post-edit now feeds the trajectory pipeline (synthesises a one-step trajectory from the edit outcome). 
 hooks_post-command does the same for command outcomes. 
 hooks_intelligence_trajectory-end ALSO bumps globalStats (was only feeding sonaCoordinator); response includes learning.globalStatsTrajectoriesDelta . 
 Every handler returns learningPath: 'trajectory-pipeline' | 'recorded-only' + an explicit note naming what fired. 
 
 Round C — Structured Distillation ( #2241 §SOTA, arXiv:2603.13017) 
 
 New module src/memory/structured-distill.ts — 4-field schema ( summary / detail / labels / paths ), rule-based deterministic extractor, embedding-ready serialiser that puts high-signal tokens at the front. 
 New corpus bench/trajectory-mrr-corpus.json — 30 paired (raw, query) trajectories. 
 New MRR harness scripts/benchmark-trajectory-mrr.mjs — bridge ONNX embedder with hash-deterministic fallback (clearly warned as degraded). 
 
 Measured proof (bridge ONNX, Xenova/all-MiniLM-L6-v2, N=30): 
 
 
 
 Metric 
 Raw 
 Distilled 
 Δ 
 
 
 
 
 MRR 
 0.0964 
 0.1367 
 +0.0403 (+41.8%) 
 
 
 Direction 
 — 
 — 
 ✅ distilled better 
 
 
 
 Direction matches arXiv:2603.13017 (+0.014 absolute on a 214K paper corpus); relative delta is larger here because the small curated corpus benefits more from labels-and-paths-first ordering. 
 Honest: a rule-based distiller cannot deliver the paper's 11× byte compression (current ratio: 0.74× — distilled is 35% bigger). The schema, corpus, harness, and serialiser are in place so a future round can plug in a learned distiller as a drop-in extractor swap and pick up that compression number while keeping this MRR direction. 
 Tests: 9 schema tests + 3 Round B wiring tests = 12 new. Affected suite 135/135. 
 Install: npx ruflo@3.10.16