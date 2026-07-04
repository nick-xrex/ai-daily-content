---
id: inbox_fc9433cd
date: 2026-07-04
source_ref: "[[00-inbox/2026-07-04/0115-ruflo-releases-v3-19-0-neural-train-routes-through-the-f2dc]]"
title: "v3.19.0 — neural train routes through the native TrainingPipeline (#2549 arc complete)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.19.0
source: ruflo-releases
published_at: 2026-07-04T00:22:46+00:00
fetched_at: 2026-07-04T01:21:38.206425+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.19.0 完成 #2549 核心改進：神經訓練現在透過 @ruvector/ruvllm 原生 TrainingPipeline 路由執行，而非僅依賴 WASM。新增 `--backend auto|native|wasm` 選項自動選路，原生路徑支援真實 epoch、損失歷史、早期停止；檢查點改進為儲存實際訓練權重（而非新建未訓練 adapter），採用 ruvllm-checkpoint v1 格式。E2E 驗證通過：最終損失 4.25e-3，6/6 測試全過，native 後端自動路由成功。"
key_points:
  - "神經訓練路由選項 --backend auto|native|wasm 自動選擇最適路徑"
  - "檢查點儲存實際訓練權重而非新建 adapter，確保復現訓練狀態"
  - "E2E 驗證完成：最終損失 4.25e-3、測試 6/6 通過"
tags: [neural-train, lora-training, backend-routing, checkpoint-management, native-pipeline]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.19.0 — neural train routes through the native TrainingPipeline (#2549 arc complete)

ruflo v3.19.0 完成 #2549 核心改進：神經訓練現在透過 @ruvector/ruvllm 原生 TrainingPipeline 路由執行，而非僅依賴 WASM。新增 `--backend auto|native|wasm` 選項自動選路，原生路徑支援真實 epoch、損失歷史、早期停止；檢查點改進為儲存實際訓練權重（而非新建未訓練 adapter），採用 ruvllm-checkpoint v1 格式。E2E 驗證通過：最終損失 4.25e-3，6/6 測試全過，native 後端自動路由成功。

### 重點
- 神經訓練路由選項 --backend auto|native|wasm 自動選擇最適路徑
- 檢查點儲存實際訓練權重而非新建 adapter，確保復現訓練狀態
- E2E 驗證完成：最終損失 4.25e-3、測試 6/6 通過

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.19.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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

</details>