---
id: inbox_ac7c66fe
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-ruflo-releases-v3-18-1-neural-status-native-ruvllm-trai-7f2e]]"
title: "v3.18.1 — neural status: native ruvllm training path no longer misreported as Unavailable (#2549)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.18.1
source: ruflo-releases
published_at: 2026-07-03T22:20:02+00:00
fetched_at: 2026-07-04T01:21:38.211505+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.18.1 修補 #2549 報告層缺陷：neural status 誤判原生 ruvllm 訓練路徑為「不可用」並提示安裝。根本成因：死變數 `_trainingBackend`（聲明未賦值）+ 跨程序全域變數陷阱（新狀態程序無法讀取共享全域狀態）。修正方案：後端改為主動能力探測（resolveTrainingBackend() 執行模組解析），對比型訓練器三態明確（Active with session counts / Available / genuinely Unavailable），安裝提示僅在真正解析失敗時出現。添加迴歸測試釘死能力約定。"
key_points:
  - "修復死變數 + 跨程序全域變數，後端改為主動探測"
  - "對比型訓練器狀態三態明確，避免虛假「Unavailable」報告"
  - "安裝提示僅在真正無法解析時出現，提升信號信噪比"
tags: [neural-status, capability-detection, cross-process-bug, regression-test]
topics: [agents.mcp]
importance: 2
novelty: 1
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.18.1 — neural status: native ruvllm training path no longer misreported as Unavailable (#2549)

ruflo v3.18.1 修補 #2549 報告層缺陷：neural status 誤判原生 ruvllm 訓練路徑為「不可用」並提示安裝。根本成因：死變數 `_trainingBackend`（聲明未賦值）+ 跨程序全域變數陷阱（新狀態程序無法讀取共享全域狀態）。修正方案：後端改為主動能力探測（resolveTrainingBackend() 執行模組解析），對比型訓練器三態明確（Active with session counts / Available / genuinely Unavailable），安裝提示僅在真正解析失敗時出現。添加迴歸測試釘死能力約定。

### 重點
- 修復死變數 + 跨程序全域變數，後端改為主動探測
- 對比型訓練器狀態三態明確，避免虛假「Unavailable」報告
- 安裝提示僅在真正無法解析時出現，提升信號信噪比

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.18.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release fixing #2549 (reported by @pacphi — exemplary report with dist-verified line numbers and a capability-vs-environment proof). 
 Fixed 
 
 neural status reported the bundled @ruvector/ruvllm training path as Unavailable — Install @ruvector/ruvllm even though the module was installed and functional. Two defects: a dead _trainingBackend variable (declared, returned, never assigned) and contrastive availability read only from an in-process global a fresh status process never populates. 
 Backend now comes from a capability probe ( resolveTrainingBackend() — module resolution, pipeline stays lazy); Contrastive Trainer has three honest states (Active with session counts / Available — ready on demand / genuinely Unavailable); the Install hint only shows on true resolution failure. 
 Dropped the 'ruvllm checkpoints enabled' claim — upstream saveCheckpoint() (@ruvector/ruvllm 2.5.6) verifiably writes no file; tracked separately. 
 
 Not in this release (follow-ups from #2549 triage) 
 
 Routing neural train through the native TrainingPipeline 
 Upstream checkpoint persistence fix 
 
 PR: #2554 · Regression test pins the capability contract in both resolve/no-resolve environments.

</details>