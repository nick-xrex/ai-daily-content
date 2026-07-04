---
id: inbox_ac7c66fe
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.18.1"
author: "ruvnet"
published_at: 2026-07-03T22:20:02+00:00
fetched_at: 2026-07-04T01:15:53.877947+00:00
content_hash: "7f2eb631106b18d5e02623fd73b86fcb20e3a830ce343f598d5acc8887939569"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.18.1 — neural status: native ruvllm training path no longer misreported as Unavailable (#2549)

Patch release fixing #2549 (reported by @pacphi — exemplary report with dist-verified line numbers and a capability-vs-environment proof). 
 Fixed 
 
 neural status reported the bundled @ruvector/ruvllm training path as Unavailable — Install @ruvector/ruvllm even though the module was installed and functional. Two defects: a dead _trainingBackend variable (declared, returned, never assigned) and contrastive availability read only from an in-process global a fresh status process never populates. 
 Backend now comes from a capability probe ( resolveTrainingBackend() — module resolution, pipeline stays lazy); Contrastive Trainer has three honest states (Active with session counts / Available — ready on demand / genuinely Unavailable); the Install hint only shows on true resolution failure. 
 Dropped the 'ruvllm checkpoints enabled' claim — upstream saveCheckpoint() (@ruvector/ruvllm 2.5.6) verifiably writes no file; tracked separately. 
 
 Not in this release (follow-ups from #2549 triage) 
 
 Routing neural train through the native TrainingPipeline 
 Upstream checkpoint persistence fix 
 
 PR: #2554 · Regression test pins the capability contract in both resolve/no-resolve environments.