---
id: inbox_7a52b714
date: 2026-07-29
source_ref: "[[00-inbox/.../inbox_7a52b714]]"
title: "Ruflo v3.32.33 — Exact Autopilot Scope and Governed Flywheel Candidates"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.33
source: ruflo-releases
published_at: 2026-07-29T13:01:42+00:00
fetched_at: 2026-07-31T01:28:28.451020+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.33 修復 CLI flag normalization mismatch 導致的 autopilot configuration 被忽略。根本原因：V3 parser 轉換 kebab-case 選項（--task-sources、--max-iterations）為 camelCase (taskSources、maxIterations)，validation layer 正確讀取 camelCase，但 CLI action 實裝卻讀舊的 kebab-case keys，導致使用者提供的值被忽略、沿用預設 source set。修復讀取 parser 的 canonical camelCase keys 同時保留 legacy keys 給直接 action 呼叫者。新增 parser-to-command integration test 和 immutable-tarball release smoke test 確保 unsupported task sources 失敗且不建立 state。Flywheel fix 同步納入：built-in proposer 可評估 bounded full-policy candidates 而無需獲得 promotion authority。版本說明：v3.32.31 因 helper manifest 簽名錯版本而 stopped；v3.32.32 修正簽名並發佈但驗證發現 flag 問題；v3.32.33 為驗證通過版本並獲得 stable npm tags。"
key_points:
  - "Parser-to-action synchronization：canonical representation (camelCase) 必須貫穿整個 pipeline，action layer 不能回頭讀 kebab-case，否則會無聲忽略使用者配置"
  - "Unsupported task sources (例如 --task-sources issues) 現失敗且不建立 state，確保 configuration 只包含有效值"
  - "Flywheel feature：built-in proposer 可安全地評估 full-policy candidates 而不獲 promotion authority，支援更細緻的 governance"
tags: [flag-normalization, configuration-validation, parser-action-sync]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Ruflo v3.32.33 — Exact Autopilot Scope and Governed Flywheel Candidates

Ruflo v3.32.33 修復 CLI flag normalization mismatch 導致的 autopilot configuration 被忽略。根本原因：V3 parser 轉換 kebab-case 選項（--task-sources、--max-iterations）為 camelCase (taskSources、maxIterations)，validation layer 正確讀取 camelCase，但 CLI action 實裝卻讀舊的 kebab-case keys，導致使用者提供的值被忽略、沿用預設 source set。修復讀取 parser 的 canonical camelCase keys 同時保留 legacy keys 給直接 action 呼叫者。新增 parser-to-command integration test 和 immutable-tarball release smoke test 確保 unsupported task sources 失敗且不建立 state。Flywheel fix 同步納入：built-in proposer 可評估 bounded full-policy candidates 而無需獲得 promotion authority。版本說明：v3.32.31 因 helper manifest 簽名錯版本而 stopped；v3.32.32 修正簽名並發佈但驗證發現 flag 問題；v3.32.33 為驗證通過版本並獲得 stable npm tags。

### 重點
- Parser-to-action synchronization：canonical representation (camelCase) 必須貫穿整個 pipeline，action layer 不能回頭讀 kebab-case，否則會無聲忽略使用者配置
- Unsupported task sources (例如 --task-sources issues) 現失敗且不建立 state，確保 configuration 只包含有效值
- Flywheel feature：built-in proposer 可安全地評估 full-policy candidates 而不獲 promotion authority，支援更細緻的 governance

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.33)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Ruflo v3.32.33 — Exact Autopilot Scope and Governed Flywheel Candidates

Ruflo v3.32.33: Autopilot Scope Enforcement at the Real CLI Boundary 
 v3.32.33 completes the Flywheel and Autopilot reliability release by enforcing 
explicit task-source validation through the same normalized flags users pass 
to the CLI. 
 The V3 parser converts kebab-case options such as --task-sources and 
 --max-iterations to taskSources and maxIterations . The initial validation 
implementation correctly rejected unsupported values at the service and MCP 
layers but read the legacy kebab-case keys in the CLI action. As a result, the 
real command ignored the supplied value and persisted the default source set. 
 This release reads the parser's canonical camelCase keys while retaining the 
legacy keys for direct action callers. A parser-to-command integration test and 
an immutable-tarball release smoke now prove that unsupported task sources fail 
without creating state. 
 Install or upgrade 
 npm install --global ruflo@3.32.33
ruflo doctor 
 Configure an exact Autopilot scope 
 ruflo autopilot config \
 --task-sources swarm-tasks,file-checklist \
 --max-iterations 77 
 Unsupported sources fail and leave the stored configuration unchanged: 
 ruflo autopilot config --task-sources issues 
 Flywheel fix included 
 The release also includes the v2 retrieval safety envelope from #2836 . The 
built-in proposer can evaluate bounded full-policy candidates without gaining 
promotion authority. 
 ruflo metaharness flywheel status
ruflo metaharness flywheel run --proposer local 
 Release lineage 
 
 v3.32.31 stopped before npm publication because its helper manifest was 
signed for the prior version. 
 v3.32.32 corrected the signed manifest and was published, but independent 
post-registry validation found the CLI flag-normalization mismatch. 
 v3.32.33 is the validated release and receives the stable npm tags.

</details>