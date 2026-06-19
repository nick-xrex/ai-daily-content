---
id: inbox_9b3424e8
date: 2026-06-18
source_ref: "[[00-inbox/2026-06-18/2200-superpowers-releases-v6-0-3-5189]]"
title: "v6.0.3"
url: https://github.com/obra/superpowers/releases/tag/v6.0.3
source: superpowers-releases
published_at: 2026-06-18T22:45:19+00:00
fetched_at: 2026-06-19T22:07:22.064923+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "superpowers v6.0.3 修正了 Subagent-Driven Development（SDD）檔案組織的關鍵問題。原本 SDD 相關檔案（task briefs、implementer reports、review diffs、progress ledger）儲存在 .git/sdd/ 目錄，但 Claude Code 將 .git/ 列為保護路徑，禁止 agent 進行寫入操作，導致實現子代理執行時被中途阻止。此版本將所有 SDD 檔案遷移至項目根目錄的自我忽略目錄 .superpowers/sdd/，自動被 git 排除在外且不出現在 commit 中。新位置透過 sdd-workspace helper 實現每 worktree 的獨立解析，確保並行開發環境的隔離。需要注意的是，git clean -fdx 命令會刪除進度帳冊，但可從 git log 恢復歷史。"
key_points:
  - "SDD 檔案從 .git/sdd/ 遷移至自我忽略的 .superpowers/sdd/ 目錄（因 Claude Code 禁止 .git/ 寫入）"
  - "透過 sdd-workspace helper 實現每 worktree 獨立解析，task briefs、implementer reports、review diffs、progress ledger 集中管理"
  - "git clean -fdx 會刪除進度帳冊，可從 git log 恢復"
tags: [superpowers, subagent-development, workflow-tooling, file-organization]
topics: [agents.mcp]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v6.0.3

superpowers v6.0.3 修正了 Subagent-Driven Development（SDD）檔案組織的關鍵問題。原本 SDD 相關檔案（task briefs、implementer reports、review diffs、progress ledger）儲存在 .git/sdd/ 目錄，但 Claude Code 將 .git/ 列為保護路徑，禁止 agent 進行寫入操作，導致實現子代理執行時被中途阻止。此版本將所有 SDD 檔案遷移至項目根目錄的自我忽略目錄 .superpowers/sdd/，自動被 git 排除在外且不出現在 commit 中。新位置透過 sdd-workspace helper 實現每 worktree 的獨立解析，確保並行開發環境的隔離。需要注意的是，git clean -fdx 命令會刪除進度帳冊，但可從 git log 恢復歷史。

### 重點
- SDD 檔案從 .git/sdd/ 遷移至自我忽略的 .superpowers/sdd/ 目錄（因 Claude Code 禁止 .git/ 寫入）
- 透過 sdd-workspace helper 實現每 worktree 獨立解析，task briefs、implementer reports、review diffs、progress ledger 集中管理
- git clean -fdx 會刪除進度帳冊，可從 git log 恢復

**原文：** [superpowers-releases](https://github.com/obra/superpowers/releases/tag/v6.0.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Subagent-Driven Development 
 
 SDD scratch files moved out of .git/ . Claude Code treats .git/ as a protected path and denies agent writes there, so an implementer subagent writing its report into .git/sdd/ got blocked mid-run. Task briefs, implementer reports, review diffs, and the progress ledger now live in a self-ignoring .superpowers/sdd/ directory in the working tree — kept out of git status and out of commits, and resolved per worktree by a shared sdd-workspace helper. One caveat: because the workspace is git-ignored working-tree scratch, git clean -fdx will delete the progress ledger; recover from git log if that happens. ( #1780 )

</details>