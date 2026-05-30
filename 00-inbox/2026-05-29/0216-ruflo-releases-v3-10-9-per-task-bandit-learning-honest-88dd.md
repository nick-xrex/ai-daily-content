---
id: inbox_37bdd54a
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.9"
author: "ruvnet"
published_at: 2026-05-29T17:37:41+00:00
fetched_at: 2026-05-30T02:16:29.845611+00:00
content_hash: "88dd31319062bc63bf197b772cbaf6277a47442a9c20be7b51a9e52041638910"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.9 — per-task bandit learning + honest intelligence labeling

Ruflo v3.10.9 — per-task bandit learning + honest intelligence labeling 
 Completes the intelligence-audit punch-list ( docs/reviews/intelligence-system-audit-2026-05-29.md ): fixes the genuinely-fixable items and documents honest ceilings for the rest — without fabricating any signals. 
 Fixed 
 
 Per-task bandit priors (ADR-142) — model-routing Beta priors are now keyed by complexity bucket (low/med/high) instead of global-per-model. Failures on one task type no longer suppress a model for all task types (the "8 Haiku failures suppress Haiku everywhere" defect). Backward-compatible schema migration (v1 flat → seed all buckets, version:2 ); proven by a per-bucket isolation test + a migration test. 
 EWC++ honesty — clarifies F_i is a heuristic embedding-importance proxy ( embedding_i2 ), not true gradient-curvature Fisher. 
 HNSW backend label — ruvector-native vs ruvector-stub-search-disabled ; isWasm()===true means the broken stub (search returns [] ), not acceleration, so a regression is now visible. 
 MicroLoRA — fixed the genuine applyUpdates() signature bug (passed a Float32Array where the WASM runtime wants a scalar learning rate). 
 
 Honest ceilings (NOT fixable in-repo — documented, not faked) 
 
 WASM-accelerated HNSW : no WASM HNSW build exists in the stack; native NAPI is already fastest (~1.9–6.5× at N=20k); "150×–12,500×" is unreachable here. 
 WASM MicroLoRA apply() : empirically still inert after the flush (Δ=0 after 200 adapts). We deliberately do not synthesize a gradient from the scalar quality to fake adaptation — that would be a fabricated signal (the same class as the Flash Math.random metric the audit removed). 
 
 All three packages published at 3.10.9 ( latest / alpha / v3alpha in lockstep). CI: 29/29 green. This closes the intelligence punch-list — every item is now fixed, shipped, or documented with an honest reason it's deferred. 
 🤖 Generated with RuFlo