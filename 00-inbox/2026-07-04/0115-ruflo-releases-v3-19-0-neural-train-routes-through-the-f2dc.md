---
id: inbox_fc9433cd
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.19.0"
author: "ruvnet"
published_at: 2026-07-04T00:22:46+00:00
fetched_at: 2026-07-04T01:15:53.870791+00:00
content_hash: "f2dc528199e6e29ebec1eea1d4262e0b11f1bc2cdc78cd1072eb35ad9fe4e3ee"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.19.0 — neural train routes through the native TrainingPipeline (#2549 arc complete)

The final piece of the #2549 saga (reported by @pacphi ): neural train now trains through @ruvector/ruvllm's native TrainingPipeline , not only the WASM path. 
 New 
 
 neural train --backend auto|native|wasm — auto (default) routes the LoRA training leg through the native pipeline when @ruvector/ruvllm resolves: real epochs, loss history, early stopping, EWC registration 
 Checkpoints carry trained weights — the previous best-effort block saved a freshly-constructed adapter's untrained weights; the native path checkpoints the pipeline that actually trained ( ruvllm-checkpoint v1 envelope on disk) 
 --backend native fails loudly when the pipeline can't run; --backend wasm preserves prior behavior exactly; SONA/ReasoningBank persistence unchanged in all modes; graceful WASM fallback when the module is absent 
 
 The complete #2549 arc 
 
 3.18.1 — neural status no longer misreports the native path (dead variable + cross-process global) 
 @ruvector/ruvllm 2.5.7 — saveCheckpoint(path) actually persists (upstream, RuVector#637) 
 3.18.2 — version floors + mkdir fix + version-gated capability reporting 
 3.19.0 — training itself routes through the native pipeline (this release) 
 
 E2E: auto → native backend, finalLoss 4.25e-3, trained checkpoint on disk. Tests 6/6. 
 PR: #2556