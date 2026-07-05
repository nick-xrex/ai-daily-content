---
id: inbox_9b5fdce4
date: 2026-07-04
source_ref: "[[00-inbox/2026-07-04/2200-ruflo-releases-v3-20-0-training-flywheel-resume-val-spl-6b16]]"
title: "v3.20.0 — training flywheel: resume, val-split, checkpoint auto-load (ruvllm 2.6.0)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.20.0
source: ruflo-releases
published_at: 2026-07-04T02:11:29+00:00
fetched_at: 2026-07-04T22:05:43.762572+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo v3.20.0 完善訓練管線，閉合訓練→檢查點→優化路由的 flywheel 循環。新增驗證分割與早停機制（neural train --val-split <frac>，輸出 bestValLoss/earlyStopped）與檢查點恢復（neural train --resume <checkpoint>，透過 ruvllm 2.6.0 的 resumeFrom() 接續輪次）。路由的 LoRA 適配器實現檢查點自動加載（首次自適應時非同步加載，非啟動路徑，自殺開關、非致命）；neural status 顯示最新檢查點及年齡。@ruvector/ruvllm 升至 2.6.0（檢查點 v2 元資料、幾何驗證、真正 resumeFrom()、最佳檢查點保留）。全部向後相容，測試 12/12 通過，啟動 0.08s 無迴歸。"
key_points:
  - "validation split + early stopping：--val-split <frac> 實現驗證與自動停止，輸出 bestValLoss 與是否觸發早停"
  - "checkpoint 恢復：--resume <checkpoint> 透過 ruvllm 2.6.0 resumeFrom() 真正接續輪次（降級為 2.5.7 重量還原）"
  - "LoRA 適配器自動加載最新檢查點（非同步、非啟動熱路徑），@ruvector/ruvllm 升至 2.6.0"
tags: [training-pipeline, checkpoint, neural-training, validation]
topics: []
importance: 4
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.20.0 — training flywheel: resume, val-split, checkpoint auto-load (ruvllm 2.6.0)

RuFlo v3.20.0 完善訓練管線，閉合訓練→檢查點→優化路由的 flywheel 循環。新增驗證分割與早停機制（neural train --val-split <frac>，輸出 bestValLoss/earlyStopped）與檢查點恢復（neural train --resume <checkpoint>，透過 ruvllm 2.6.0 的 resumeFrom() 接續輪次）。路由的 LoRA 適配器實現檢查點自動加載（首次自適應時非同步加載，非啟動路徑，自殺開關、非致命）；neural status 顯示最新檢查點及年齡。@ruvector/ruvllm 升至 2.6.0（檢查點 v2 元資料、幾何驗證、真正 resumeFrom()、最佳檢查點保留）。全部向後相容，測試 12/12 通過，啟動 0.08s 無迴歸。

### 重點
- validation split + early stopping：--val-split <frac> 實現驗證與自動停止，輸出 bestValLoss 與是否觸發早停
- checkpoint 恢復：--resume <checkpoint> 透過 ruvllm 2.6.0 resumeFrom() 真正接續輪次（降級為 2.5.7 重量還原）
- LoRA 適配器自動加載最新檢查點（非同步、非啟動熱路徑），@ruvector/ruvllm 升至 2.6.0

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.20.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Native training pipeline gains real epochs-across-runs and closes the train→checkpoint→better-routing loop. 
 
 neural train --val-split &lt;frac&gt; — validation + early stopping (surfaces bestValLoss/earlyStopped) 
 neural train --resume &lt;checkpoint&gt; — continues from the restored epoch via ruvllm 2.6.0 resumeFrom() (degrades to 2.5.7 weight-restore) 
 Checkpoint auto-load — routing's lazy LoRA adapter loads the newest checkpoint on first adaptation use (off the startup hot path, kill-switch, non-fatal) 
 neural status shows latest checkpoint + age 
 @ruvector/ruvllm 2.6.0 (RuVector#638): checkpoint v2 metadata + geometry validation, true resumeFrom(), best-checkpoint retention; floors bumped &gt;=2.6.0 
 
 Tests 12/12 · startup 0.08s (no regression) · PR #2557

</details>