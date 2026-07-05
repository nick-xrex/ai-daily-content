---
id: inbox_9b5fdce4
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.20.0"
author: "ruvnet"
published_at: 2026-07-04T02:11:29+00:00
fetched_at: 2026-07-04T22:00:22.960123+00:00
content_hash: "6b164e4e4bf4d5885886116ead21ffa90cf78518c8cd4e4605c250c6ec7396df"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.20.0 — training flywheel: resume, val-split, checkpoint auto-load (ruvllm 2.6.0)

Native training pipeline gains real epochs-across-runs and closes the train→checkpoint→better-routing loop. 
 
 neural train --val-split &lt;frac&gt; — validation + early stopping (surfaces bestValLoss/earlyStopped) 
 neural train --resume &lt;checkpoint&gt; — continues from the restored epoch via ruvllm 2.6.0 resumeFrom() (degrades to 2.5.7 weight-restore) 
 Checkpoint auto-load — routing's lazy LoRA adapter loads the newest checkpoint on first adaptation use (off the startup hot path, kill-switch, non-fatal) 
 neural status shows latest checkpoint + age 
 @ruvector/ruvllm 2.6.0 (RuVector#638): checkpoint v2 metadata + geometry validation, true resumeFrom(), best-checkpoint retention; floors bumped &gt;=2.6.0 
 
 Tests 12/12 · startup 0.08s (no regression) · PR #2557