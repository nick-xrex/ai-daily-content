---
id: inbox_e2e76bc7
date: 2026-05-29
source_ref: "[[00-inbox/2026-05-29/0216-ruflo-releases-v3-10-6-memory-routing-statusline-bug-fi-4f02]]"
title: "v3.10.6 — memory, routing &amp; statusline bug fixes (#2219 #2226 #2222 #2221 #2215)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.6
source: ruflo-releases
published_at: 2026-05-29T12:56:04+00:00
fetched_at: 2026-05-30T02:25:00.426919+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.6 修復 5 個重現性 bug。最嚴重的 #2219：Node 24/26 上 better-sqlite3 預建二進制缺失，optional deps 無聲失敗導致 AgentDB 降級為非持久化後端，資料無法寫入磁盤。修復：覆蓋 better-sqlite3 >= 12.8.0（支援 Node 20–26 預構）並在 root 與發佈 wrapper 中同時設置（root override 不自動傳播的教訓 #2112），加新 CI 守衛防止回歸。其他修復涵蓋 #2226 pattern-store/search 後端分離、#2222 route feedback 未持久化、#2221 statusline 全域安裝版本號錯誤、#2215 flashAttention 狀態矛盾。新增 bug-cluster-2219-2226.test.ts 5/5 回歸測試和 statusline 漂移守衛 8/8。"
key_points:
  - "Node 24/26 上 optional deps 無聲失敗 → better-sqlite3 預構缺失 → 資料無聲丟失；修復覆蓋至 >=12.8.0 + 新 CI 守衛"
  - "Root override 不傳播至發佈 wrapper（#2112 教訓重現）→ 需在兩處同時設置"
  - "多後端狀態不同步（pattern-store vs pattern-search）→ 修復統一讀寫路徑、加 getEntry 水合化"
tags: [nodejs-compatibility, sqlite, optional-dependencies, state-synchronization, regression-tests]
topics: []
importance: 4
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.6 — memory, routing & statusline bug fixes (#2219 #2226 #2222 #2221 #2215)

Ruflo v3.10.6 修復 5 個重現性 bug。最嚴重的 #2219：Node 24/26 上 better-sqlite3 預建二進制缺失，optional deps 無聲失敗導致 AgentDB 降級為非持久化後端，資料無法寫入磁盤。修復：覆蓋 better-sqlite3 >= 12.8.0（支援 Node 20–26 預構）並在 root 與發佈 wrapper 中同時設置（root override 不自動傳播的教訓 #2112），加新 CI 守衛防止回歸。其他修復涵蓋 #2226 pattern-store/search 後端分離、#2222 route feedback 未持久化、#2221 statusline 全域安裝版本號錯誤、#2215 flashAttention 狀態矛盾。新增 bug-cluster-2219-2226.test.ts 5/5 回歸測試和 statusline 漂移守衛 8/8。

### 重點
- Node 24/26 上 optional deps 無聲失敗 → better-sqlite3 預構缺失 → 資料無聲丟失；修復覆蓋至 >=12.8.0 + 新 CI 守衛
- Root override 不傳播至發佈 wrapper（#2112 教訓重現）→ 需在兩處同時設置
- 多後端狀態不同步（pattern-store vs pattern-search）→ 修復統一讀寫路徑、加 getEntry 水合化

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.6)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ruflo v3.10.6 — memory, routing &amp; statusline bug-fix release 
 Five reproducible bugs reported by external contributors ( @pacphi , @casparml , @HF-teamdev ), each verified against source and covered by a regression test. Thanks to all three for the detailed, well-traced reports. 
 🔴 #2219 — Silent write loss on Node 24/26 
 agentdb declares better-sqlite3 as an optional dependency at ^11.8.1 , which has no prebuilt binary for Node 24/25/26. On those runtimes the optional native build fails silently (optional deps never error), and AgentDB drops to a non-persistent backend — stores appear to succeed but never land on disk. 
 Fix: override better-sqlite3 → &gt;=12.8.0 (ships Node 20–26 prebuilds) in both the root umbrella and the ruflo wrapper (root overrides don't propagate to the published wrapper — the #2112 lesson). A new CI guard ( audit-better-sqlite3-override.mjs ) keeps the override pinned so this can't regress. 
 
 If you installed globally on Node 24/26 before this release: npm i -g ruflo@latest restores the native backend. 
 
 🔴 #2226 — agentdb_pattern-store / agentdb_pattern-search never agreed 
 The store and search MCP tools hit disjoint backends , so a stored pattern was never returned by search. Two paths fixed: 
 
 Controller present: bridgeSearchPatterns now reads LocalReasoningBank.findSimilar / getAll — the same backend the store writes to. 
 Controller absent (the common case): the memory-store-fallback search now hydrates each entry's content via getEntry before matching — listEntries returns metadata only (see #2014 ), so the substring scan previously matched nothing. 
 
 🟠 #2222 — route feedback was a no-op 
 Feedback applied the Q-learner update in memory, but the CLI process exits before the autoSaveInterval flush fires, so route-learning never persisted across invocations. Fix: explicit awaited router.saveModel() after feedback. 
 🟡 #2221 — Statusline showed RuFlo V3.6 on global installs 
 getPkgVersion() never probed the global npm root, so npm i -g ruflo fell back to the hard-coded default version. Fix: derive the global node_modules dir from process.execPath (no npm spawn — statusline renders often); covers nvm/mise and Windows layouts. 
 🟡 #2215 — flashAttention reported contradictory state 
 system_info emitted a hard-coded flashAttention: false while hooks_intelligence reported the live probe. Fix: system_info now runs the same getFlashAttention() probe as the authoritative path, so the two tools can't disagree. 
 
 Verification 
 
 New regression suite bug-cluster-2219-2226.test.ts — 5/5 (incl. end-to-end store→search roundtrip) 
 Statusline drift guard — 8/8 (regenerated .cjs byte-identical to generator) 
 tsc clean; CI 29/29 green including the new better-sqlite3 override guard 
 
 Install 
 npm i -g ruflo@latest # or @3.10.6 
npx ruflo@latest --version # → 3.10.6 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) published at 3.10.6 with latest / alpha / v3alpha in lockstep. 
 🤖 Generated with RuFlo

</details>