---
id: inbox_d654d2bc
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-ruflo-releases-v3-18-2-native-ruvllm-checkpoints-end-to-ec96]]"
title: "v3.18.2 — native ruvllm checkpoints end-to-end (#2549 complete)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.18.2
source: ruflo-releases
published_at: 2026-07-03T23:03:51+00:00
fetched_at: 2026-07-04T01:21:38.210203+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.18.2 完成 #2549 檢查點持久化層：正式整合 @ruvector/ruvllm@2.5.7 上游修正，確保 LoRA 檢查點實際寫入磁碟。版本鎖定 ruvllm >=2.5.7（跨 npm override、pnpm override 三層路徑保證一致性）；修復目錄建立缺陷（JS fallback 拋 ENOENT 導致檢查點未寫入檔案系統）；版本閘控能力報告（neural status 僅在 ruvllm >=2.5.7 時才宣傳檢查點功能，避免虛假承諾）。驗證產出：48KB ruvllm-checkpoint v1 格式檔案。"
key_points:
  - "版本鎖定 @ruvector/ruvllm >=2.5.7 於全部安裝路徑（npm/pnpm override）"
  - "修復 mkdir + 檔案寫入缺陷，檢查點確實落地磁碟"
  - "版本閘控：能力報告與實際環境版本繫結，避免承諾無法交付功能"
tags: [checkpoint-persistence, version-management, capability-gating, npm-override]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.18.2 — native ruvllm checkpoints end-to-end (#2549 complete)

ruflo v3.18.2 完成 #2549 檢查點持久化層：正式整合 @ruvector/ruvllm@2.5.7 上游修正，確保 LoRA 檢查點實際寫入磁碟。版本鎖定 ruvllm >=2.5.7（跨 npm override、pnpm override 三層路徑保證一致性）；修復目錄建立缺陷（JS fallback 拋 ENOENT 導致檢查點未寫入檔案系統）；版本閘控能力報告（neural status 僅在 ruvllm >=2.5.7 時才宣傳檢查點功能，避免虛假承諾）。驗證產出：48KB ruvllm-checkpoint v1 格式檔案。

### 重點
- 版本鎖定 @ruvector/ruvllm >=2.5.7 於全部安裝路徑（npm/pnpm override）
- 修復 mkdir + 檔案寫入缺陷，檢查點確實落地磁碟
- 版本閘控：能力報告與實際環境版本繫結，避免承諾無法交付功能

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.18.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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

</details>