---
id: inbox_bc4298c6
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-ruflo-releases-v3-27-0-daemon-flywheel-fix-cross-worktr-19ff]]"
title: "v3.27.0 — daemon flywheel fix (cross-worktree dedup + global launch budget)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.27.0
source: ruflo-releases
published_at: 2026-07-14T04:47:07+00:00
fetched_at: 2026-07-14T22:10:02.251613+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.27.0 修復 daemon 飛輪 bug（#2661）：N 個 git worktree 原本各自排程 N 個無上限 AI 工作者啟動。解決方案跨三層：1) git-workspace-identity.ts 透過 `git rev-parse --git-common-dir` 解析穩定儲存庫 ID（獨立於逐次 worktree 路徑）；2) ai-job-dedup.ts 以 sha256(repositoryId, head, workerType, configHash) 為鍵進行跨 worktree 任務去重，備份於 ~/.claude-flow/ai-jobs.json；3) global-ai-budget.ts 提供全機器全 daemon 共享的全域啟動預算（最大並發 + 逐小時上限），即使兩個 daemon 爭搶同一鍵也充當硬性後擋。AI 工作者改為選擇加入；daemon stop --all 停止所有 daemon 實例。Hook-handler 回退修復已驗證。"
key_points:
  - "git-workspace-identity.ts：透過 `git rev-parse --git-common-dir` 解析穩定 repositoryId（跨 worktree 共享，獨立於路徑）"
  - "ai-job-dedup.ts：去重鍵 sha256(repositoryId, head, workerType, configHash)，備份於 ~/.claude-flow/ai-jobs.json，實現跨 worktree 去重"
  - "global-ai-budget.ts：全機器全 daemon 共享預算（max concurrent + hourly cap），作為最終後擋即使 daemon 競爭；AI workers opt-in；daemon stop --all 停止所有實例"
tags: [ruflo, daemon, dedup, distributed-architecture, budget]
topics: []
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.27.0 — daemon flywheel fix (cross-worktree dedup + global launch budget)

Ruflo v3.27.0 修復 daemon 飛輪 bug（#2661）：N 個 git worktree 原本各自排程 N 個無上限 AI 工作者啟動。解決方案跨三層：1) git-workspace-identity.ts 透過 `git rev-parse --git-common-dir` 解析穩定儲存庫 ID（獨立於逐次 worktree 路徑）；2) ai-job-dedup.ts 以 sha256(repositoryId, head, workerType, configHash) 為鍵進行跨 worktree 任務去重，備份於 ~/.claude-flow/ai-jobs.json；3) global-ai-budget.ts 提供全機器全 daemon 共享的全域啟動預算（最大並發 + 逐小時上限），即使兩個 daemon 爭搶同一鍵也充當硬性後擋。AI 工作者改為選擇加入；daemon stop --all 停止所有 daemon 實例。Hook-handler 回退修復已驗證。

### 重點
- git-workspace-identity.ts：透過 `git rev-parse --git-common-dir` 解析穩定 repositoryId（跨 worktree 共享，獨立於路徑）
- ai-job-dedup.ts：去重鍵 sha256(repositoryId, head, workerType, configHash)，備份於 ~/.claude-flow/ai-jobs.json，實現跨 worktree 去重
- global-ai-budget.ts：全機器全 daemon 共享預算（max concurrent + hourly cap），作為最終後擋即使 daemon 競爭；AI workers opt-in；daemon stop --all 停止所有實例

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.27.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights 
 Daemon flywheel fix ( #2661 ) — opt-in AI workers, a global cross-daemon launch budget, cross-worktree job dedup, and daemon stop --all . Fixes the cardinality bug where N git worktrees of one repository scheduled N independent, uncapped AI worker launches. 
 
 git-workspace-identity.ts — resolves a stable repositoryId shared across all worktrees of one repo (via git rev-parse --git-common-dir ), separate from the per-worktree path. 
 ai-job-dedup.ts — cross-worktree job dedup keyed on sha256(repositoryId, head, workerType, configHash) , backed by a shared registry at ~/.claude-flow/ai-jobs.json . 
 global-ai-budget.ts — a global launch budget (max concurrent + hourly cap) shared by every daemon on the machine, so the dedup optimization has a hard backstop even when two daemons race the same key. 
 AI workers are now opt-in rather than auto-launching. 
 daemon stop --all stops every daemon instance, not just the one bound to the current cwd. 
 
 Hook-handler fallback fix — the inline hook-handler.cjs fallback template (used when copying the real package helper fails) now spawns the funnel-refresh helper from session-restore , matching the fix already shipped in the hand-maintained helper. 
 Verified after publish 
 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) live at 3.27.0 on latest / alpha / v3alpha . 
 Confirmed the macOS jetsam-kill/kernel-panic statusline fix ( #2448 ) is intact: a real npx @claude-flow/cli@3.27.0 init produces a settings.json with zero npx @claude-flow/cli@latest invocations in any hook or the statusline — everything resolves a local binary directly via node . 
 
 Packages 
 
 
 
 Package 
 Version 
 
 
 
 
 @claude-flow/cli 
 3.27.0 
 
 
 claude-flow 
 3.27.0 
 
 
 ruflo 
 3.27.0 
 
 
 
 Follow-up 
 
 Full technical writeup of the daemon flywheel bug + fix: https://gist.github.com/ruvnet/f4cda824aaf58e1f2dae72368e692220 
 Issue thread + implementation-vs-spec gap notes: #2661 
 Follow-up fixes landed in v3.27.1–v3.27.4: marketplace-checkout install validation ( dist/src/index.js check + npx fallback for the funnel/advisor refresh), version-display max-candidate selection, baked-in version fallback for pure-npx renders, and persistent AgentDB memory on by default at init time.

</details>