---
id: inbox_61d05b86
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.14"
author: "ruvnet"
published_at: 2026-05-30T15:39:35+00:00
fetched_at: 2026-05-30T18:00:42.590205+00:00
content_hash: "e479fa630b82df837ea4d1c6976f4aca217e4a2a7ff3ebec17a2429dbaf8968b"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.14 — self-learning wiring (ADR-074, closes #2245)

Wires up the self-learning subsystem the reporter found was reporting success but persisting nothing queryable ( #2245 ). Three CLI-side wirings + honest multi-path output + a proof harness. 
 What's fixed 
 
 hooks_task-completed {trainPatterns: true} now invokes the real SONA + EWC++ trajectory pipeline (was a stub returning patternsLearned: 0 ). Returns learningPath: 'trajectory-pipeline' | 'recorded-only' so callers know what happened. 
 signalsProcessed was a dead counter — initialized 3×, read 1×, incremented 0× anywhere. Now wired into bridgeStoreEntry so every memory-bridge write counts. loadPersistedStats also restores patternsLearned + signalsProcessed so a process restart no longer zeroes the learning history. 
 hooks_pretrain now writes per-pattern rows into the neural store (via new storeNeuralPatterns ), so neural_patterns list reflects them. Response surfaces both patternsBundled + patternsIndexed + sources.stores . 
 
 Honest multi-path messaging (per the goal-condition) 
Every learning-adjacent surface declares the path it took and the store(s) it wrote to. The task-completed description lists the three paths explicitly: (a) trainPatterns:true for one-step learning, (b) hooks_intelligence_trajectory-* for multi-step, (c) memory_store for storage without learning. 
 Adversarial hardening ( #2241 ASI06) 
Basic content sanitization on task-completed content before it feeds SONA (strip ASCII control chars, cap to 4 KB). 
 Proof 
 
 __tests__/self-learning-2245.test.ts — 9 tests across EASY / MEDIUM / COMPLEX categories. CI gate. 
 scripts/benchmark-self-learning.mjs — 5 sections (A–E), writes a committed run JSON. Latest run: signalsProcessed +10, trained=10/10 at ~18 ms/call, pretrain stored=10/listed=10, multi-step persisted=5/sonaUpdate=5. All passed. 
 Reproduction guide: v3/docs/learning/self-learning-2245-proof.md 
 ADR: v3/docs/adr/ADR-074-self-learning-wiring-2245.md 
 
 Install: npx ruflo@3.10.14 
 Tracked for round 2 (not in this release) 
Unify the 4 stat aggregators (globalStats / memory_bridge / hooks_metrics / neural_patterns); wire post-edit / post-command to feed the trajectory pipeline; Structured Distillation ( #2241 ) of trajectory content for 11× compression + better MRR.