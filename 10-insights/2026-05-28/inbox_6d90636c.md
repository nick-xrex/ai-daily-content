---
id: inbox_6d90636c
date: 2026-05-28
source_ref: "[[00-inbox/2026-05-28/0139-claude-code-releases-v2-1-153-6146]]"
title: "v2.1.153"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.153
source: claude-code-releases
published_at: 2026-05-28T00:52:08+00:00
fetched_at: 2026-05-28T01:43:34.924613+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.153 發佈，包含 40+ 項功能改進與回歸修復。核心改動：Git LFS 跳過選項、npm 自動更新失敗通知、狀態欄指令支援 COLUMNS/LINES 環境變數適應終端寬度、Agent 自動完成建議原生斜杠指令與打包技能。關鍵修復包括有狀態 MCP 伺服器重連迴圈、API 閘道認證洩漏、記憶體過度使用（多 GB）、Windows 安裝失敗報告、daemon 陳舊問題。模型選擇器現保存預設設定，降低重複選擇。"
key_points:
  - "v2.1.153 修復 40+ 錯誤：有狀態 MCP 伺服器重連迴圈、API 閘道認證洩漏、記憶體過度使用"
  - "狀態欄指令支援 COLUMNS/LINES 環境變數，scripts 可自適應終端寬度（新 pattern）"
  - "Agent 自動完成改進、模型選擇器保存預設、Windows 更新失敗自動還原"
tags: [claude-code, release, mcp-servers, terminal-scripting, bugfix]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.153

Claude Code v2.1.153 發佈，包含 40+ 項功能改進與回歸修復。核心改動：Git LFS 跳過選項、npm 自動更新失敗通知、狀態欄指令支援 COLUMNS/LINES 環境變數適應終端寬度、Agent 自動完成建議原生斜杠指令與打包技能。關鍵修復包括有狀態 MCP 伺服器重連迴圈、API 閘道認證洩漏、記憶體過度使用（多 GB）、Windows 安裝失敗報告、daemon 陳舊問題。模型選擇器現保存預設設定，降低重複選擇。

### 重點
- v2.1.153 修復 40+ 錯誤：有狀態 MCP 伺服器重連迴圈、API 閘道認證洩漏、記憶體過度使用
- 狀態欄指令支援 COLUMNS/LINES 環境變數，scripts 可自適應終端寬度（新 pattern）
- Agent 自動完成改進、模型選擇器保存預設、Windows 更新失敗自動還原

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.153)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added skipLfs option to github / git plugin marketplace sources to skip Git LFS downloads during clone and update 
 Claude Code now shows a one-time notice when your npm global install can't auto-update; /doctor lists the fixes 
 Status line commands now receive COLUMNS and LINES environment variables so scripts can size output to the terminal width 
 claude agents : autocomplete in the dispatch input now suggests native slash commands and bundled skills, not just project skills 
 claude agents : PR column now shows PR #N for a single PR or N PRs for multiple 
 claude doctor now shows the result of your last update attempt 
 Combined the separate "needs authentication" startup notifications for MCP servers and connectors into a single message 
 macOS: background agents now appear as "Claude Code" in Privacy &amp; Security and keep their permission grants across upgrades 
 Fixed stateful MCP servers without the optional GET SSE stream reconnect-looping on tools/list (regression in v2.1.147) 
 Fixed a regression where a custom API gateway could receive the user's Anthropic OAuth credential instead of the gateway's own token 
 Fixed subagent (Agent tool) frontmatter MCP servers ignoring --strict-mcp-config , --bare , remote mode, enterprise managed MCP config, and managed-settings MCP server allow/deny policies 
 --strict-mcp-config no longer strips inline mcpServers from explicitly-passed agent definitions ( --agents / SDK agents ), and blocked subagent MCP servers now surface a visible warning 
 Fixed the Windows PowerShell installer reporting "Installation complete!" when installation actually failed 
 Fixed claude update installing the latest version instead of the configured release channel's version for npm installations 
 Fixed excessive memory usage (multiple GB) when resuming a session by transcript file path on machines with many stored sessions 
 Fixed claude agents and claude --bg running on a stale daemon started before binary-takeover support, even after upgrading 
 Fixed a hang where the CLI could fail to exit when stdin was closed without EOF in stream-json mode, leaving a stale session marker behind 
 Fixed malformed file:// links in Claude's responses not being clickable in the terminal 
 Fixed claude --help rendering unwrapped output on terminals narrower than 92 columns 
 Fixed MCP tool progress notifications not rendering in the collapsed tool view 
 Fixed Agent tool with subagent_type: 'claude' running in an undocumented temporary worktree, which could silently discard outputs written to gitignored paths 
 /bg while Claude is responding now continues the response in the background session instead of dropping it 
 Fixed /btw keyboard shortcuts becoming unresponsive in background sessions while a task is running 
 Fixed background sessions writing temp files to $CLAUDE_JOB_DIR triggering a "sensitive file" permission prompt 
 Fixed recovering a background agent whose working directory was deleted showing a truncated stack trace instead of a clear error message 
 Fixed EnterWorktree not being available immediately in background sessions (previously required ToolSearch first) 
 Fixed cmd+k in iTerm2/Terminal.app not repainting attached background sessions 
 Fixed the IME candidate window appearing at the bottom of the screen instead of next to the input caret in attached background sessions on Windows 
 Fixed background-color bleed when attaching to a background agent from 256-color-only terminals after the agent had rendered file diffs 
 Fixed /copy and copy-on-select silently failing to update the system clipboard when attached to a background session inside tmux 
 Fixed opening claude agents with Remote Control enabled leaving zombie session entries on the Code tab after exiting 
 Fixed /rename in background sessions not updating the session banner immediately 
 Fixed Windows update rollback: if a Windows update fails, Claude Code now restores the original executable by copy and tells you how to recover 
 [VSCode] Fixed Claude Code processes not shutting down cleanly when VS Code closed on Windows, causing false "unclean exit" reports and orphaned MCP servers 
 /model now saves your selection as the default for new sessions (matching the IDE). Press s in the picker to switch models for the current session only. 
 If you customized the modelPicker:setAsDefault keybinding, rename it to modelPicker:thisSessionOnly in keybindings.json (the d action was replaced by s )

</details>