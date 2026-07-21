---
id: inbox_c66d3980
date: 2026-07-18
source_ref: "[[00-inbox/.../inbox_c66d3980]]"
title: "v3.32.8 — CI unblock, memory_search fix, version lockstep"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.8
source: ruflo-releases
published_at: 2026-07-18T22:31:28+00:00
fetched_at: 2026-07-21T01:04:51.595909+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.8 發布，修復三個關鍵問題與驗證既知修補。首先修復 pnpm 鎖檔漂移：@claude-flow/security 版本在 package.json（^3.0.0-alpha.12）與 pnpm-lock.yaml（^3.0.0-alpha.10）間不同步，導致 --frozen-lockfile CI 持續失敗，已重新生成同步。其次修正 MCP memory_search 工具在省略 namespace 參數時返回 0 結果的迴歸（第三次出現），問題根源是工具處理器強制將 omitted namespace 轉為字串 'default' 而非保持 undefined，阻擋搜尋層的 namespace || 'all' 預設邏輯，已新增回歸測試於工具邊界層。第三處理版本鎖步漂移，將 claude-flow、@claude-flow/cli、ruflo 三包對齊至 3.32.8，latest/alpha/v3alpha dist-tags 已同步。另驗證 Worktree daemon 任務隊列飽和問題已於 v3.27.4/v3.28.0 修復（改採監督選舉 + 工作區租賃 + 全局電路斷路器設計）。"
key_points:
  - "pnpm-lock.yaml 版本漂移導致凍結鎖檔 CI 驗證反覆失敗（@claude-flow/security α10 vs α12），已重新生成"
  - "MCP memory_search 工具在省略 namespace 時返回 0 結果：工具處理器需轉發 undefined 而非強制 'default' 字串，已新增邊界層測試防止重複"
  - "claude-flow、@claude-flow/cli、ruflo 三包版本鎖步達成 3.32.8，dist-tags（latest/alpha/v3alpha）同步"
tags: [ruflo, mcp, lockfile-management, version-lockstep]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.8 — CI unblock, memory_search fix, version lockstep

Ruflo v3.32.8 發布，修復三個關鍵問題與驗證既知修補。首先修復 pnpm 鎖檔漂移：@claude-flow/security 版本在 package.json（^3.0.0-alpha.12）與 pnpm-lock.yaml（^3.0.0-alpha.10）間不同步，導致 --frozen-lockfile CI 持續失敗，已重新生成同步。其次修正 MCP memory_search 工具在省略 namespace 參數時返回 0 結果的迴歸（第三次出現），問題根源是工具處理器強制將 omitted namespace 轉為字串 'default' 而非保持 undefined，阻擋搜尋層的 namespace || 'all' 預設邏輯，已新增回歸測試於工具邊界層。第三處理版本鎖步漂移，將 claude-flow、@claude-flow/cli、ruflo 三包對齊至 3.32.8，latest/alpha/v3alpha dist-tags 已同步。另驗證 Worktree daemon 任務隊列飽和問題已於 v3.27.4/v3.28.0 修復（改採監督選舉 + 工作區租賃 + 全局電路斷路器設計）。

### 重點
- pnpm-lock.yaml 版本漂移導致凍結鎖檔 CI 驗證反覆失敗（@claude-flow/security α10 vs α12），已重新生成
- MCP memory_search 工具在省略 namespace 時返回 0 結果：工具處理器需轉發 undefined 而非強制 'default' 字串，已新增邊界層測試防止重複
- claude-flow、@claude-flow/cli、ruflo 三包版本鎖步達成 3.32.8，dist-tags（latest/alpha/v3alpha）同步

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.8)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.8 — CI unblock, memory_search fix, version lockstep

v3.32.8 — CI unblock, memory_search fix, version lockstep 
 Fixed 
 
 CI-breaking lockfile drift ( #2719 , #2717 ): v3/pnpm-lock.yaml was pinned to @claude-flow/security@^3.0.0-alpha.10 while package.json had moved to ^3.0.0-alpha.12 , failing every --frozen-lockfile CI job ( Type Check V3 and others) on every PR since the drift landed. Regenerated via pnpm install --lockfile-only . 
 MCP memory_search namespace regression ( #2646 , third occurrence of #1123 / #1131 ): omitting the optional namespace parameter returned 0 results even when data existed across multiple namespaces, because the tool handler coerced an omitted namespace to the literal string 'default' instead of leaving it undefined so the search layer's own namespace || 'all' fallback could fire. Fixed with a regression test that asserts what the tool handler forwards to the search layer directly, so this class of regression is caught at the tool boundary going forward. 
 Package version lockstep (surfaced by #2703 ): claude-flow had drifted to 3.32.2 while @claude-flow/cli / ruflo were at 3.32.7, failing the Plugin package install-safety CI check. All three packages are now back in lockstep at 3.32.8 . 
 
 Verified as already fixed (no code change this release) 
 
 [P0] Worktree daemon fanout quota exhaustion ( #2661 ): confirmed already fixed same-day via #2662 / #2663 (shipped v3.27.4/v3.28.0) — repository-scoped supervisor election, workspace leases, and a global AI-launch budget with a circuit breaker replaced the old per-worktree dedup that let every Git worktree spin up its own set of scheduled Claude-powered workers. The tracking issue had stayed open because the fix commits didn't use GitHub's auto-close keyword; closed now with verification (40/43 tests passing; the 3 failures are a Windows symlink-privilege sandbox limitation, not real bugs). 
 
 Registry 
 
 latest , alpha , and v3alpha dist-tags are synced to 3.32.8 across @claude-flow/cli , claude-flow , and ruflo ( #2703 ). 
 
 Full Changelog : v3.32.7...v3.32.8

</details>