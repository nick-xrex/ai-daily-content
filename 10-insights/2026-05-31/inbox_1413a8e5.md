---
id: inbox_1413a8e5
date: 2026-05-31
source_ref: "[[00-inbox/2026-05-31/1801-ruflo-releases-v3-10-31-model-router-daemon-trigger-bug-2cdf]]"
title: "v3.10.31 — model router + daemon trigger bug-fix patch (#2250, #2251)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.31
source: ruflo-releases
published_at: 2026-05-31T14:49:49+00:00
fetched_at: 2026-05-31T18:06:48.257818+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.31 修復兩個 Claude Flow model router 與 daemon trigger 的關鍵缺陷。#2250 問題：router escalation 不當覆蓋 Thompson bandit 策略，導致不確定性閾值設置過高（0.6 vs 0.15），造成 Opus 在瑣碎任務被誤選 ~40%、Haiku 永不被選。修復加入目標均值比較（selected_mean − 0.10）與信心度檢查（α+β ≥ 5 AND mean ≥ 0.45）；新增環境變數 CLAUDE_FLOW_MAX_UNCERTAINTY 覆蓋。#2251 問題：daemon trigger -w race with headless init，修復透過 headlessInitPromise 確保初始化完成後才觸發。新增 4 個回歸測試覆蓋 Opus 壓制率、冷啟動保留、環境覆蓋、異步承諾順序。"
key_points:
  - "Thompson bandit escalation 邏輯修正：不確定性公式結構性 >0.6，超過 0.15 閾值 → 改為條件性 escalation（目標均值 OR 信心度檢查）"
  - "daemon trigger race condition 消除：awaits headlessInitPromise before checking headlessAvailable"
  - "CLAUDE_FLOW_MAX_UNCERTAINTY 環境變數提供靈活覆蓋機制"
tags: [ruflo, claude-flow, model-router, thompson-bandit, daemon-trigger, bug-fix]
topics: [foundation_models.claude]
importance: 4
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.31 — model router + daemon trigger bug-fix patch (#2250, #2251)

Ruflo v3.10.31 修復兩個 Claude Flow model router 與 daemon trigger 的關鍵缺陷。#2250 問題：router escalation 不當覆蓋 Thompson bandit 策略，導致不確定性閾值設置過高（0.6 vs 0.15），造成 Opus 在瑣碎任務被誤選 ~40%、Haiku 永不被選。修復加入目標均值比較（selected_mean − 0.10）與信心度檢查（α+β ≥ 5 AND mean ≥ 0.45）；新增環境變數 CLAUDE_FLOW_MAX_UNCERTAINTY 覆蓋。#2251 問題：daemon trigger -w race with headless init，修復透過 headlessInitPromise 確保初始化完成後才觸發。新增 4 個回歸測試覆蓋 Opus 壓制率、冷啟動保留、環境覆蓋、異步承諾順序。

### 重點
- Thompson bandit escalation 邏輯修正：不確定性公式結構性 >0.6，超過 0.15 閾值 → 改為條件性 escalation（目標均值 OR 信心度檢查）
- daemon trigger race condition 消除：awaits headlessInitPromise before checking headlessAvailable
- CLAUDE_FLOW_MAX_UNCERTAINTY 環境變數提供靈活覆蓋機制

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.31)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Bug fixes 
 #2250 — model router escalation overrode Thompson bandit 
 Trained opus-suppressed priors were discarded by an "escalate one tier up" step that fired on ~every trivial route (the uncertainty formula was structurally &gt;0.6, gate at 0.15). Reporter ( @grym3s ) measured opus selected ~40% on trivial tasks, haiku never selected. 
 Fix in v3/@claude-flow/cli/src/ruvector/model-router.ts : 
 
 Escalation now skips when (a) target mean is meaningfully worse than selected ( &lt; selected_mean − 0.10 ), OR (b) selected has confident+decent posterior ( α+β ≥ 5 AND mean ≥ 0.45 ) 
 Cold-start Beta(1,1) priors fail both checks → unlearned routers preserve original conservative behavior 
 New env override: CLAUDE_FLOW_MAX_UNCERTAINTY=0.0..1.0 
 
 #2251 — daemon trigger -w &lt;worker&gt; raced headless init 
 Constructor kicked off initHeadlessExecutor() fire-and-forget. On-demand daemon trigger called triggerWorker() immediately after construction, raced the init, and fell through to the local stub in ~2ms. Scheduled fires were unaffected (long-running daemon never raced). Reporter ( @shaharKeisarApps ). 
 Fix in v3/@claude-flow/cli/src/services/worker-daemon.ts : 
 
 New headlessInitPromise field capturing the constructor's init promise 
 triggerWorker() awaits it before checking headlessAvailable 
 
 Regression guard 
 v3/@claude-flow/cli/__tests__/issue-2250-2251-regression.test.ts — 4 new tests: 
 
 Loads reporter's exact suppressed-opus prior, asserts opus rate &lt;20% AND haiku selected ≥1 time over 50 trivial routes 
 Cold-start preservation 
 Env override 
 Deferred-promise harness proves executeWorker() cannot fire until headlessInitPromise resolves 
 
 All 12 router + daemon tests pass. TypeScript clean. 
 Install 
 npx ruflo@latest # or @alpha / @v3alpha 
npx @claude-flow/cli@latest
npx claude-flow@latest 
 All three packages published to npm, all three dist-tags ( latest , alpha , v3alpha ) pointing at 3.10.31. 
 What's NOT in this release 
 5-dataset BEIR benchmark work (TREC-COVID ingest still in flight) → ships as 3.10.32.

</details>