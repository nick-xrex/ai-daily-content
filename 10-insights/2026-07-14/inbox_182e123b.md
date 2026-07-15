---
id: inbox_182e123b
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-ruflo-releases-v3-28-0-2661-root-fix-repository-supervi-0679]]"
title: "v3.28.0 — #2661 root-fix: repository supervisor, telemetry, budget CLI, migration warning"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.28.0
source: ruflo-releases
published_at: 2026-07-14T05:36:54+00:00
fetched_at: 2026-07-14T22:10:02.248583+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.28.0 閉合 #2661 的四個根本修復缺口（PR #2663）：1) 儲存庫層級 supervisor + worktree leases（workspace-lease.ts、repo-supervisor.ts）— 每個儲存庫恰好一個 daemon 被選為 supervisor 擁有循環 AI 工作者排程，其他 worktree 作為租用參與者（15 分鐘 TTL 心跳）執行廉價本地工作者；2) 結構化逐次啟動 token 遙測透過 `claude --print --output-format json` 且 parseClaudePrintJsonEnvelope() 解析（schema 不符降級為「無使用捕獲」，不破壞既有輸出）；3) `ruflo daemon budget show|pause|resume` CLI 獨立控制；4) 一次性升級遷移警告。另修復 statusline-generator.ts 瞬時依賴，內聯最小版本解析避免 semver 引入。新增 54 項測試，636 項相關測試通過。"
key_points:
  - "workspace-lease.ts + repo-supervisor.ts 實現儲存庫層級 supervisor 選舉 + 15 分鐘 TTL 租用心跳機制，保證每個儲存庫恰好一個 supervisor daemon"
  - "parseClaudePrintJsonEnvelope() 解析結構化遙測（claude --print --output-format json），schema 不符時降級為「無使用捕獲」而非中斷"
  - "daemon status --all 新增 \"Repository Supervisors\" 面板；ruflo daemon budget show|pause|resume 提供獨立控制介面"
tags: [ruflo, daemon, supervisor-pattern, telemetry, budget]
topics: []
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.28.0 — #2661 root-fix: repository supervisor, telemetry, budget CLI, migration warning

Ruflo v3.28.0 閉合 #2661 的四個根本修復缺口（PR #2663）：1) 儲存庫層級 supervisor + worktree leases（workspace-lease.ts、repo-supervisor.ts）— 每個儲存庫恰好一個 daemon 被選為 supervisor 擁有循環 AI 工作者排程，其他 worktree 作為租用參與者（15 分鐘 TTL 心跳）執行廉價本地工作者；2) 結構化逐次啟動 token 遙測透過 `claude --print --output-format json` 且 parseClaudePrintJsonEnvelope() 解析（schema 不符降級為「無使用捕獲」，不破壞既有輸出）；3) `ruflo daemon budget show|pause|resume` CLI 獨立控制；4) 一次性升級遷移警告。另修復 statusline-generator.ts 瞬時依賴，內聯最小版本解析避免 semver 引入。新增 54 項測試，636 項相關測試通過。

### 重點
- workspace-lease.ts + repo-supervisor.ts 實現儲存庫層級 supervisor 選舉 + 15 分鐘 TTL 租用心跳機制，保證每個儲存庫恰好一個 supervisor daemon
- parseClaudePrintJsonEnvelope() 解析結構化遙測（claude --print --output-format json），schema 不符時降級為「無使用捕獲」而非中斷
- daemon status --all 新增 "Repository Supervisors" 面板；ruflo daemon budget show|pause|resume 提供獨立控制介面

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.28.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights 
 Closes the four remaining root-fix gaps from #2661 (PR #2663 ): 
 
 Repository-level supervisor + worktree leases ( workspace-lease.ts , repo-supervisor.ts ) — exactly one daemon per repository is elected supervisor and owns the recurring AI-worker schedule; every other worktree stays a lease-only participant (15-min TTL heartbeat) running cheap local-only workers. An explicit daemon trigger --headless still bypasses the gate (one-off user action, still budget/dedup-governed). 
 Structured per-launch token telemetry — claude --print --output-format json , parsed leniently via parseClaudePrintJsonEnvelope() , receipted through GlobalAiBudget.recordUsage() . Any schema mismatch degrades to "no usage captured," never breaks existing analysis-output parsing. 
 ruflo daemon budget show|pause|resume — independently scriptable budget control surface. 
 One-time upgrade migration warning — a pre-existing multi-daemon fleet with AI workers already enabled warns exactly once ever. 
 
 daemon status --all gains a "Repository Supervisors" panel. 
 Also fixes a real transitive-dependency fragility: statusline-generator.ts no longer pulls in the semver package just to resolve the CLI's own version — inlined a minimal, dependency-free version resolver instead. 
 Test plan 
 
 54 new tests across workspace-lease , repo-supervisor , claude-print-envelope , global-ai-budget , daemon-migration-warning-2661 
 636 relevant tests passing locally (services + daemon + commands-deep) 
 Full CI green on PR #2663 (one flaky, unrelated timing test in @claude-flow/hooks 's trajectory-graph smoke passed on rerun) 
 
 Packages 
 
 
 
 Package 
 Version 
 
 
 
 
 @claude-flow/cli 
 3.28.0 
 
 
 claude-flow 
 3.28.0 
 
 
 ruflo 
 3.28.0

</details>