---
id: inbox_0c1cca6a
date: 2026-05-29
source_ref: "[[00-inbox/2026-05-29/0216-claude-code-releases-v2-1-157-e206]]"
title: "v2.1.157"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.157
source: claude-code-releases
published_at: 2026-05-29T20:20:38+00:00
fetched_at: 2026-05-30T02:20:22.257390+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.157 發布，核心改進包括 .claude/skills 目錄內的插件自動加載（無需市集）、claude plugin init 指令快速建立插件、工作樹中途切換功能、settings.json 代理欄位支援。此版本修復 40+ 項問題，包括影像損毀不崩潰、背景代理完成後解鎖工作樹便於清理、IDE 整合的快捷鍵與終端渲染、剪貼簿在 tmux 中的複製迴歸。新增工具決策遙測與流程關鍵字觸發設定。實務意義：開發者無需依賴市集即可加載本地插件；多代理背景工作流更穩定可靠。"
key_points:
  - ".claude/skills 目錄內插件自動載入，無需市集依賴"
  - "claude plugin init 指令支持新插件快速建立；settings.json 代理欄位可通過 --agent 旗標覆蓋"
  - "工作樹現在在代理完成後解鎖，便於 git worktree remove/prune 清理；修復背景代理遺孤問題"
tags: [claude-code, v2.1.157, plugin-system, worktree, agent-management]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.157

Claude Code v2.1.157 發布，核心改進包括 .claude/skills 目錄內的插件自動加載（無需市集）、claude plugin init 指令快速建立插件、工作樹中途切換功能、settings.json 代理欄位支援。此版本修復 40+ 項問題，包括影像損毀不崩潰、背景代理完成後解鎖工作樹便於清理、IDE 整合的快捷鍵與終端渲染、剪貼簿在 tmux 中的複製迴歸。新增工具決策遙測與流程關鍵字觸發設定。實務意義：開發者無需依賴市集即可加載本地插件；多代理背景工作流更穩定可靠。

### 重點
- .claude/skills 目錄內插件自動載入，無需市集依賴
- claude plugin init 指令支持新插件快速建立；settings.json 代理欄位可通過 --agent 旗標覆蓋
- 工作樹現在在代理完成後解鎖，便於 git worktree remove/prune 清理；修復背景代理遺孤問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.157)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Plugins in .claude/skills directories are now automatically loaded, no marketplace required 
 Added claude plugin init &lt;name&gt; to scaffold a new plugin in .claude/skills 
 Added autocomplete for /plugin arguments: subcommands, installed plugin names, and plugins from known marketplaces 
 claude agents : the agent field in settings.json is now honored for dispatched sessions, with --agent &lt;name&gt; to override it 
 EnterWorktree can now switch between Claude-managed worktrees mid-session 
 tool_decision telemetry events now include tool_parameters (bash commands, MCP/skill names) when OTEL_LOG_TOOL_DETAILS=1 
 Worktrees managed by Claude are now left unlocked when the agent finishes, so git worktree remove / prune can clean them up 
 Fixed unprocessable images (zero-byte, corrupt) attached via paste, MCP, or dialog crashing the request instead of becoming a text placeholder 
 Fixed sandbox network permission prompts appearing in auto and bypass-permissions mode when using the desktop app, IDE extensions, or SDK 
 Fixed claude agents completed sessions not retiring when an idle subagent was still parked or had leaked a backgrounded shell 
 Fixed claude agents pressing Esc not cancelling a slow "opening...", leaving the list unresponsive 
 Fixed background agent worktrees under .claude/worktrees/ being orphaned after the 30-day job retention sweep 
 Fixed background sessions re-attached after a sleep/wake not telling the model the correct date 
 Fixed copy-on-select in claude agents not reaching the system clipboard inside tmux with set-clipboard on (regression in 2.1.153) 
 Fixed --resume not reporting background subagents that were running when the previous Claude Code process exited 
 Fixed the --resume session picker leaving its contents on the terminal after exiting in fullscreen mode 
 Fixed --worktree and --worktree --tmux returning to the canonical repo root instead of the current linked worktree 
 Fixed the /model picker showing an incorrect "Newer version available" hint when the selected model is already the newest in its family; the pinned-model row now shows the model's description instead of its raw ID 
 Fixed literal markdown markers (backticks, asterisks) appearing in the in-progress message text in fullscreen mode 
 Fixed the terminal freezing after approving the managed-settings security dialog at startup 
 Fixed a rare duplicate line appearing in scrollback after the terminal UI redraws 
 Fixed right-click paste duplicating the clipboard in the VS Code, Cursor, and Windsurf integrated terminals 
 WSL: fixed image paste ( alt+v keybinding), screenshot paste on Windows 11, and added support for dragging images from Windows Explorer 
 Improved performance of long and resumed conversations by eliminating redundant message-rendering recomputations 
 /terminal-setup now disables GPU acceleration in VS Code/Cursor/Windsurf integrated terminals to prevent garbled-text rendering 
 The Feature of the Week credit-claim status now appears as a notification in the status area instead of a line above the prompt 
 claude agents : slash-command autocomplete in the dispatch input now matches substrings 
 Removed the "bash commands will be sandboxed" startup banner — sandbox status still shows in /status and when a command is blocked 
 Removed the "/ide for ..." startup hint toast 
 [IDE] Fixed clicking Stop while a background subagent is running not actually stopping it 
 [VSCode] Fixed the fast mode indicator not appearing on Opus 4.8 
 Pressing backspace right after a workflow trigger keyword now dismisses the workflow request (same as alt+w) instead of deleting a character 
 Added a "Workflow keyword trigger" setting in /config to stop the word "workflow" in a prompt from triggering a dynamic workflow

</details>