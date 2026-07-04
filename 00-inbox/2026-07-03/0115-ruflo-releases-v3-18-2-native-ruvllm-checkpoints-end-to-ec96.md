---
id: inbox_d654d2bc
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.18.2"
author: "ruvnet"
published_at: 2026-07-03T23:03:51+00:00
fetched_at: 2026-07-04T01:15:53.876741+00:00
content_hash: "ec96c0e741c5c54ec25d3e1f4e5fac397fea10319b49636697cde140fb860efd"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.18.2 — native ruvllm checkpoints end-to-end (#2549 complete)

Completes the #2549 arc: ruflo now actively uses the checkpoint persistence shipped in @ruvector/ruvllm@2.5.7 (RuVector#637). 
 Changed 
 
 Version floors @ruvector/ruvllm &gt;=2.5.7 in the ruflo wrapper overrides, root npm overrides, and v3 pnpm overrides — every install path is guaranteed the fixed version 
 neural train checkpoints actually land : LoRAAdapter.saveCheckpoint now creates parent directories before writing — the JS fallback threw ENOENT on missing dirs and silently returned false, so the best-effort checkpoint never materialized even after the upstream fix 
 Version-gated capability reporting : neural status shows 'native @ruvector/ruvllm pipeline + disk checkpoints' only when the resolved ruvllm is &gt;=2.5.7 — never advertises persistence a stale install can't deliver 
 Dev-tree hygiene: removed a stale npm-installed @ruvector/ruvllm@0.2.4 directory that had shadowed pnpm resolution since April 
 
 Proof 
 neural train -p coordination -e 2
→ .claude-flow/neural/lora-checkpoint-&lt;ts&gt;.json (format: ruvllm-checkpoint v1, 48KB)
 
 #2549 status: neural-status reporting fixed (3.18.1) → upstream persistence fixed (@ruvector/ruvllm 2.5.7) → ruflo wired end-to-end (this release). Remaining follow-up: routing neural train fully through the native TrainingPipeline. 
 PR: #2555 · Upstream: ruvnet/RuVector#637