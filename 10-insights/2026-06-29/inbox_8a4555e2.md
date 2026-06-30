---
id: inbox_8a4555e2
date: 2026-06-29
source_ref: "[[00-inbox/2026-06-29/2218-ruflo-releases-v3-15-0-agenticow-cow-memory-branching-4-68c8]]"
title: "v3.15.0 — agenticow COW memory branching (4 MCP tools, +162-byte branches)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.15.0
source: ruflo-releases
published_at: 2026-06-29T16:05:08+00:00
fetched_at: 2026-06-29T23:12:02.416473+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo 發布 v3.15.0，整合 agenticow@~0.2.3 Copy-On-Write 記憶體分支技術，新增 4 個 MCP 工具（agenticow_branch、agenticow_checkpoint、agenticow_rollback、agenticow_promote）。解決了 v3.14.4 中 3.3GB tarball 膨脹回歸，單筆分支大小恆定在 162 字節（無論基礎大小），比完整副本小 3,214~181,930 倍（取決於資料大小）。Branch 操作約 10ms 固定成本，Rollback 為 O(edits)。通過 7/7 單元測試、8/8 bash 煙霧測試、108/108 CI 檢查。可選依賴設計確保無 runtime 硬依賴，缺失時優雅降級。"
key_points:
  - "162 字節分支大小常數，vs 完整副本 3,214×~181,930× 更小"
  - "4 個 MCP 工具：branch（O(1) fork）、checkpoint（復原點）、rollback（O(edits)）、promote（原子合併）"
  - "解決 Darwin loops git-worktree 全量副本累積的 3.3GB 膨脹，支援 per-user 記憶體個性化"
tags: [agenticow, mcp-tools, copy-on-write, memory-branching, workflow-optimization]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.15.0 — agenticow COW memory branching (4 MCP tools, +162-byte branches)

Ruflo 發布 v3.15.0，整合 agenticow@~0.2.3 Copy-On-Write 記憶體分支技術，新增 4 個 MCP 工具（agenticow_branch、agenticow_checkpoint、agenticow_rollback、agenticow_promote）。解決了 v3.14.4 中 3.3GB tarball 膨脹回歸，單筆分支大小恆定在 162 字節（無論基礎大小），比完整副本小 3,214~181,930 倍（取決於資料大小）。Branch 操作約 10ms 固定成本，Rollback 為 O(edits)。通過 7/7 單元測試、8/8 bash 煙霧測試、108/108 CI 檢查。可選依賴設計確保無 runtime 硬依賴，缺失時優雅降級。

### 重點
- 162 字節分支大小常數，vs 完整副本 3,214×~181,930× 更小
- 4 個 MCP 工具：branch（O(1) fork）、checkpoint（復原點）、rollback（O(edits)）、promote（原子合併）
- 解決 Darwin loops git-worktree 全量副本累積的 3.3GB 膨脹，支援 per-user 記憶體個性化

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.15.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's new in 3.15.0 
 This is a MINOR release adding agenticow@~0.2.3 — Copy-On-Write memory branching — as 4 new MCP tools. No breaking changes; the new dep is in optionalDependencies with graceful-degraded fallbacks. 
 New MCP tools (4) 
 
 
 
 Tool 
 Purpose 
 
 
 
 
 agenticow_branch 
 COW-fork a base .rvf memory at ~162 bytes regardless of base size 
 
 
 agenticow_checkpoint 
 Freeze a labelled restore point that survives close+reopen 
 
 
 agenticow_rollback 
 Discard edits since the most recent checkpoint, O(edits) not O(N) 
 
 
 agenticow_promote 
 Atomically merge a branch's edits (with tombstones) into a base or target 
 
 
 
 Read-through semantics on every branch: parent ∪ edits, child wins . Persisted via &lt;file&gt;.agenticow.json lineage manifest. 
 Motivation 
 v3.14.4 uncovered a 3.3 GB tarball-bloat regression where Darwin loops' git-worktree-per-agent pattern accumulated full-copy snapshots. agenticow is the structural fix — 162-byte branches instead of full copies. 
 Measured perf vs. published claims 
 Full bench harness: scripts/bench-agenticow.mjs 
Findings doc: docs/agenticow/findings.md ( gist mirror ) 
 
 
 
 Claim 
 Result 
 Detail 
 
 
 
 
 162-byte branches 
 ✅ Confirmed exact 
 Constant at N=1k, 10k, 50k 
 
 
 ≥3,000× smaller than full-copy 
 ✅ Confirmed and exceeded 
 3,214× at N=1k → 181,930× at N=50k 
 
 
 "0.5ms branch" 
 ❌ Not reproduced 
 Measured ~10 ms (fixed cost, not size-proportional) 
 
 
 "83× faster" 
 ❌ Crossover N≈30k 
 Below crossover, full-copy wins 
 
 
 
 We measured, not parroted — per CLAUDE.md's source-of-truth rule. 
 Architectural constraint (zero hard runtime dep) 
 agenticow is in optionalDependencies . When missing, every tool returns {success: true, degraded: true, reason: 'agenticow-not-found'} and exits 0. Same posture as the metaharness integration (ADR-150). Verified by the no-metaharness-smoke CI gate on every PR. 
 What this enables in ruflo 
 
 Darwin loops without worktree bloat — branch-per-iteration at 162 B instead of full git-worktree clones 
 Speculative agent edits with O(1) rollback — checkpoint → try → rollback if the JUDGE step rejects 
 Per-user / per-session memory personalization — federation primitive for fork-and-merge 
 A/B routing experiments on real memory — branch candidate routers, bench each, promote the winner 
 
 Tests 
 
 7/7 vitest unit tests pass ( v3/@claude-flow/cli/__tests__/agenticow-tools.test.ts ) 
 8/8 bash smoke contract pass ( scripts/smoke-agenticow.sh ) 
 108/108 CI checks green on PR #2500 before merge 
 
 Install / upgrade 
 npx ruflo@latest # 3.15.0 
npx @claude-flow/cli@latest # 3.15.0 
npx claude-flow@latest # 3.15.0 
 Or via package.json : 
 {
 "dependencies" : {
 "@claude-flow/cli" : " ^3.15.0 " 
 }
} 
 Verified npm dist-tags 
 @claude-flow/cli latest=3.15.0 alpha=3.15.0 v3alpha=3.15.0
claude-flow latest=3.15.0 alpha=3.15.0 v3alpha=3.15.0
ruflo latest=3.15.0 alpha=3.15.0 v3alpha=3.15.0
 
 Related 
 
 PR #2500 — feat(mcp): integrate agenticow@~0.2.3 — COW memory branching (4 MCP tools) 
 PR #2501 — chore(release): 3.14.4 → 3.15.0

</details>