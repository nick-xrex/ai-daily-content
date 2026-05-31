---
id: inbox_68084ff0
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.15"
author: "ruvnet"
published_at: 2026-05-30T16:09:24+00:00
fetched_at: 2026-05-30T18:00:42.588157+00:00
content_hash: "531c1a0fac49b5194b1e1dcc497b8b71ded9b939fc3ba8ad92741c7f1ebe78f1"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.15 — unified learning stats (ADR-075)

Resolves the "four contradictory stat sources" item ADR-074 deferred to a future round. 
 The four sources turned out not to be duplicates — they authoritatively measure four different layers (globalStats = trajectory-pipeline counters, sonaCoordinator = in-process SONA, memory-bridge = AgentDB entries, neural-patterns = neural store rows). So the fix is to aggregate the view , not the store. 
 New surface 
 
 getUnifiedLearningStats() — returns all 4 sub-views with each sub-view naming its source path 
 hooks_intelligence_unified-stats MCP tool exposing it 
 getMemoryBridgeStats() + getNeuralStoreStats() — exported helpers 
 A consistency block that flags cross-store drift (e.g. globalStats reports N patterns but neural_patterns is empty) instead of silently disagreeing 
 
 Verification 
 
 7 cross-store consistency tests 
 Benchmark §F observed: global=10/11 tracks SONA, bridge=10 rows, neural=10, sona.available=true, 1 consistency note correctly flagging the pretrain-vs-neural-store gap 
 123/123 across unified-stats + self-learning + mcp-tools-deep 
 
 Install: npx ruflo@3.10.15