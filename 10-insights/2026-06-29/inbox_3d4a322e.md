---
id: inbox_3d4a322e
date: 2026-06-29
source_ref: "[[00-inbox/2026-06-29/2331-ruflo-releases-v3-16-1-fix-daemon-close-lockfile-race-w-9015]]"
title: "v3.16.1 — fix(daemon): close lockfile race window (#2484)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.16.1
source: ruflo-releases
published_at: 2026-06-29T23:58:55+00:00
fetched_at: 2026-07-02T00:15:15.477479+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.16.1 修復 Claude Code 會話中多重 daemon 實例生成的性能問題（#2484）。問題現象：使用者 EDortta 報告每個 Claude Code 會話產生 4 個相同的 daemon 進程，4 個並發會話累積約 1.7 GB swap 記憶體（16 GB 機器）。根本原因：launcher lockfile 去重中的 TOCTOU 窗口——鎖在 \"is daemon running?\" 檢查後釋放，但在 startBackgroundDaemon 前，並發呼叫者可落入窗口 (lock release ← → PID file write)，各自產生獨立 background daemon。修復：貫穿整個生成生命週期持有鎖，lock-loser 必見已持鎖或已寫入 PID（零窗口）；3 個明確釋放路徑（early-return、background、foreground）確保所有退出路徑清理。77/77 vitest 通過、6/6 新迴歸測試通過、101/101 CI 檢查綠。"
key_points:
  - "TOCTOU 競態：lock release 與 PID-file write 間隙導致並發 daemon 分叉（每會話 ×4）"
  - "修復策略：持鎖覆蓋完整生成生命週期，lock-loser 必見 lock 或 PID（消除空窗）；3 路明確釋放"
  - "實際影響：4 並發會話 swap 耗用 1.7 GB（16 GB 機器上可觀察）— 迴歸測試 daemon-lockfile-race-2484.test.ts 涵蓋"
tags: [daemon-lifecycle, toctou-race, lockfile-sync, performance-regression, memory-leak]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.16.1 — fix(daemon): close lockfile race window (#2484)

ruflo v3.16.1 修復 Claude Code 會話中多重 daemon 實例生成的性能問題（#2484）。問題現象：使用者 EDortta 報告每個 Claude Code 會話產生 4 個相同的 daemon 進程，4 個並發會話累積約 1.7 GB swap 記憶體（16 GB 機器）。根本原因：launcher lockfile 去重中的 TOCTOU 窗口——鎖在 "is daemon running?" 檢查後釋放，但在 startBackgroundDaemon 前，並發呼叫者可落入窗口 (lock release ← → PID file write)，各自產生獨立 background daemon。修復：貫穿整個生成生命週期持有鎖，lock-loser 必見已持鎖或已寫入 PID（零窗口）；3 個明確釋放路徑（early-return、background、foreground）確保所有退出路徑清理。77/77 vitest 通過、6/6 新迴歸測試通過、101/101 CI 檢查綠。

### 重點
- TOCTOU 競態：lock release 與 PID-file write 間隙導致並發 daemon 分叉（每會話 ×4）
- 修復策略：持鎖覆蓋完整生成生命週期，lock-loser 必見 lock 或 PID（消除空窗）；3 路明確釋放
- 實際影響：4 並發會話 swap 耗用 1.7 GB（16 GB 機器上可觀察）— 迴歸測試 daemon-lockfile-race-2484.test.ts 涵蓋

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.16.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's fixed in 3.16.1 
 PATCH bump for issue #2484 — Multiple daemon instances spawned per Claude Code session . EDortta reported 4 identical daemon start --foreground --quiet processes per Claude Code session, accumulating to ~1.7 GB swap on a 16 GB machine with 4 concurrent sessions. 
 Root cause 
 TOCTOU window in the launcher's lockfile dedup. The lock was held for the "is a daemon running?" check but released BEFORE startBackgroundDaemon (which forks the real background process and writes the PID file). Concurrent callers could land in the window between lock-release and PID-file-write, see neither lock nor PID, and each fork their own background daemon. 
 Fix 
 Hold the lock through the entire spawn lifecycle. The lock-loser now ALWAYS sees either a held lock OR a populated PID file — never the empty window. Three explicit release paths (early-return, background, foreground) so every exit path cleans up. 
 Verified 
 
 Build clean ( tsc ) 
 77/77 vitest pass across 3 daemon-related test files 
 6/6 new regression-test cases pass ( daemon-lockfile-race-2484.test.ts ) 
 101/101 CI checks green on PR #2505 before merge 
 
 Install / upgrade 
 npx ruflo@latest # 3.16.1 
npx @claude-flow/cli@latest # 3.16.1 
npx claude-flow@latest # 3.16.1 
 npm dist-tags 
 @claude-flow/cli latest=3.16.1 alpha=3.16.1 v3alpha=3.16.1
claude-flow latest=3.16.1 alpha=3.16.1 v3alpha=3.16.1
ruflo latest=3.16.1 alpha=3.16.1 v3alpha=3.16.1
 
 Related 
 
 PR #2505 — fix(daemon): hold lockfile through spawn lifecycle 
 PR #2506 — chore(release): 3.16.0 → 3.16.1 
 Issue #2484 — Multiple daemon instances spawned per Claude Code session 
 Builds on the lockfile work originally added for #2407 (39 zombie daemons → ~8.5 GiB) — this closes the remaining race window that left the older fix incomplete.

</details>