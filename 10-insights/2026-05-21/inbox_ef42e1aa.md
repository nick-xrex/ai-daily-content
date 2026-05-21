---
id: inbox_ef42e1aa
date: 2026-05-21
source_ref: "[[00-inbox/2026-05-21/0917-claude-code-releases-v2-1-146-aa24]]"
title: "v2.1.146"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.146
source: claude-code-releases
published_at: 2026-05-21T01:51:52+00:00
fetched_at: 2026-05-21T09:21:44.203732+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 釋出 v2.1.146，將 /simplify 指令重新命名為 /code-review 並新增 effort level 參數（如 /code-review high）；修復 Windows PowerShell 工具失效問題（winget 及 Microsoft Store 安裝版本的 command line invalid 錯誤、MCP 分頁伺服器資源列表截斷、Windows Terminal 後台會話全屏閃爍等多項穩定性問題；改進自動更新器網路重試機制、大檔案編輯 diff 渲染效能；修復背景任務 worktree 清理、權限提示重複出現等邊界情況；Auto mode 不再在使用者或技能明確依賴時抑制 AskUserQuestion。"
key_points:
  - "/code-review 指令新增 effort level 參數控制審查深度"
  - "修復 Windows PowerShell 從 winget/Microsoft Store 安裝時的 command line invalid 錯誤（v2.1.124 迴歸）"
  - "改進自動更新器的網路暫時故障重試機制，不再立即失敗"
tags: [claude-code, release, windows-fix, mcp, bugfix]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.146

Claude Code 釋出 v2.1.146，將 /simplify 指令重新命名為 /code-review 並新增 effort level 參數（如 /code-review high）；修復 Windows PowerShell 工具失效問題（winget 及 Microsoft Store 安裝版本的 command line invalid 錯誤、MCP 分頁伺服器資源列表截斷、Windows Terminal 後台會話全屏閃爍等多項穩定性問題；改進自動更新器網路重試機制、大檔案編輯 diff 渲染效能；修復背景任務 worktree 清理、權限提示重複出現等邊界情況；Auto mode 不再在使用者或技能明確依賴時抑制 AskUserQuestion。

### 重點
- /code-review 指令新增 effort level 參數控制審查深度
- 修復 Windows PowerShell 從 winget/Microsoft Store 安裝時的 command line invalid 錯誤（v2.1.124 迴歸）
- 改進自動更新器的網路暫時故障重試機制，不再立即失敗

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.146)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Renamed /simplify to /code-review with an optional effort level (e.g. /code-review high ) 
 Auto mode no longer suppresses AskUserQuestion when the user or a skill explicitly relies on it 
 Fixed Windows PowerShell tool failing with "command line is invalid" when pwsh is installed via winget or the Microsoft Store (regression in v2.1.124) 
 Fixed MCP resources/list , resources/templates/list , and prompts/list dropping items past page 1 on paginating servers 
 Fixed full-screen strobing in attached background sessions on Windows Terminal while Claude is streaming 
 Fixed the auto-updater status line not showing your current version when an update fails 
 Fixed on Windows, removing a background-job worktree no longer follows NTFS junctions into the main repo 
 Fixed /background refusing sessions whose only typed input was a skill or custom slash command 
 Fixed backgrounded sessions re-prompting for tool permissions you already granted with "don't ask again" 
 Fixed /theme color editor and "New custom theme" dialogs not responding to Esc 
 Fixed an uncaught exception at the end of streaming sessions when running via the Agent SDK 
 Fixed forceLoginOrgUUID and forceLoginMethod managed-settings policies not being enforced against third-party-provider and API-key sessions 
 Fixed GNOME Terminal right-click and middle-click paste not inserting text 
 Fixed CLAUDE_CODE_SUBAGENT_MODEL not being forwarded to child processes in multi-agent sessions 
 Improved auto-updater reliability: native version checks and downloads now retry transient network failures instead of failing immediately 
 Improved diff rendering performance for large file edits

</details>