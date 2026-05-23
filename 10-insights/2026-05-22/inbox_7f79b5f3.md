---
id: inbox_7f79b5f3
date: 2026-05-22
source_ref: "[[00-inbox/2026-05-22/0047-claude-code-releases-v2-1-149-8fdf]]"
title: "v2.1.149"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.149
source: claude-code-releases
published_at: 2026-05-22T22:09:29+00:00
fetched_at: 2026-05-23T00:51:43.453499+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.149 發布，新增 `/usage` 命令按類別分解限制用量（skills、subagents、plugins、per-MCP server），`/diff` 支援鍵盤導航（上下箭頭、j/k、PgUp/PgDn）。修復多項安全和功能缺陷：PowerShell 內建 cd 函數繞過權限檢查、git worktree 沙箱誤允許整個 repo root 讀取、Bash find 在大目錄樹耗盡 macOS vnode 導致系統當機、權限分析器 PWD/OLDPWD 追蹤失效等。GFM task list 支援、enterprise MCP 連接器整合。累計 20+ bug 修復。"
key_points:
  - "`/usage` 新增 skills/subagents/plugins/per-MCP 成本分類檢視，幫助使用者診斷配額用量"
  - "修復 PowerShell cd 內建函數權限繞過（cd.., cd\, cd~），允許讀取工作區外檔案"
  - "修復 Bash find 在大目錄樹耗盡 macOS vnode，導致主機系統當機"
tags: [claude-code-release, security-fixes, bug-fixes]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.149

Claude Code v2.1.149 發布，新增 `/usage` 命令按類別分解限制用量（skills、subagents、plugins、per-MCP server），`/diff` 支援鍵盤導航（上下箭頭、j/k、PgUp/PgDn）。修復多項安全和功能缺陷：PowerShell 內建 cd 函數繞過權限檢查、git worktree 沙箱誤允許整個 repo root 讀取、Bash find 在大目錄樹耗盡 macOS vnode 導致系統當機、權限分析器 PWD/OLDPWD 追蹤失效等。GFM task list 支援、enterprise MCP 連接器整合。累計 20+ bug 修復。

### 重點
- `/usage` 新增 skills/subagents/plugins/per-MCP 成本分類檢視，幫助使用者診斷配額用量
- 修復 PowerShell cd 內建函數權限繞過（cd.., cd\, cd~），允許讀取工作區外檔案
- 修復 Bash find 在大目錄樹耗盡 macOS vnode，導致主機系統當機

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.149)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 /usage now shows a per-category breakdown of what's driving your limits usage — skills, subagents, plugins, and per-MCP-server cost 
 /diff detail view can now be scrolled with the keyboard (arrows, j / k , PgUp / PgDn , Space , Home / End ) 
 Markdown output now renders GFM task list checkboxes ( - [ ] todo / - [x] done ) instead of plain bullets 
 Enterprise: added the allowAllClaudeAiMcps managed setting to load claude.ai cloud MCP connectors alongside managed-mcp.json 
 Fixed a PowerShell permission bypass: built-in cd functions ( cd.. , cd\ , cd~ , X: ) changed the working directory undetected, letting a later command read outside the workspace 
 Fixed the sandbox write allowlist in git worktrees covering the entire main repository root instead of only the shared .git directory (with hooks/ and config denied) 
 Fixed PowerShell prefix/wildcard allow rules (e.g. PowerShell(dotnet.exe build *) ) not pre-approving native executables and scripts 
 Fixed a permission-analysis gap where the parser trusted stale variable-tracking values for PWD / OLDPWD / DIRSTACK across cd / pushd / popd 
 Fixed find in the Bash tool exhausting the macOS system file/vnode table and crashing the host on large directory trees 
 Fixed the managed-settings approval dialog leaving the terminal frozen after accepting at startup 
 Fixed /ultraplan and remote session creation failing with "Could not capture uncommitted changes" when the working tree has no real changes 
 Fixed otelHeadersHelper failing silently when the script path contains spaces; helper failures are now reported in /doctor and the debug log 
 Fixed the thinking spinner staying amber across tool calls and onto fresh thinking bursts 
 Fixed collapsed Bash output reporting the wrong hidden-line count for outputs with many short lines 
 Fixed slash-command argument-hint clipping trailing typed characters when the hint overflows the input box 
 Fixed argument-hint and progressive arg suggestions not appearing after Tab-completing a skill whose frontmatter name: differs from its directory basename 
 Fixed the status bar showing the user's baseline /effort setting instead of the effort level applied by skill/agent effort: frontmatter 
 Fixed Ctrl+O transcript view freezing at the moment it was opened instead of tailing new messages 
 Fixed editing a recalled prompt-history entry losing the edit when navigating further up/down with arrow keys 
 Fixed /config exit summary reporting phantom changes to auto-compact and theme when toggling unrelated settings 
 Fixed /insights crashing when cached session-meta files are missing optional fields 
 Fixed malformed PowerShell and History tool calls with missing input being misclassified as reads in transcript collapsing 
 Fixed renaming a Remote Control session from claude.ai or the Claude mobile app not updating the local session name for claude --resume 
 Fixed a race where a just-submitted prompt could appear twice in the up-arrow history 
 Fixed tapping the "Jump to bottom" pill in fullscreen mode not dismissing it immediately 
 Improved /feedback reports to include the conversation that happened before context compaction, making issues from earlier in long sessions easier to triage

</details>