---
id: inbox_49f0f6fe
date: 2026-06-03
source_ref: "[[00-inbox/2026-06-03/0028-claude-code-releases-v2-1-162-d3e7]]"
title: "v2.1.162"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.162
source: claude-code-releases
published_at: 2026-06-03T21:31:35+00:00
fetched_at: 2026-06-04T00:31:52.229237+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.162 發布，引入多項改善與修復。新增 `claude agents --json` 輸出 waitingFor 欄位顯示阻擋原因（如權限提示）；Grep/Glob 工作在原生編譯版本上可用；斜線指令自動補全改為點擊填入而非立即執行；Remote Control 改為持久化 footer 顯示。修復 Windows 路徑識別、MCP 逾時設定、LSP workspace symbol、終端顯示寬度、背景服務通訊等多個問題，提升整體穩定性與用戶體驗。"
key_points:
  - "claude agents --json 新增 waitingFor 欄位，顯示會話阻擋原因"
  - "修復 Windows 路徑識別問題：反斜線 (~\、\\server\share) 與大小寫變體現在正確匹配權限規則"
  - "MCP 子 1000ms 逾時設定現改為忽略，回退到預設值，修復全量工具呼叫被中止的問題"
tags: [claude-code, release, tooling, stability-fix]
topics: []
importance: 4
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.162

Claude Code v2.1.162 發布，引入多項改善與修復。新增 `claude agents --json` 輸出 waitingFor 欄位顯示阻擋原因（如權限提示）；Grep/Glob 工作在原生編譯版本上可用；斜線指令自動補全改為點擊填入而非立即執行；Remote Control 改為持久化 footer 顯示。修復 Windows 路徑識別、MCP 逾時設定、LSP workspace symbol、終端顯示寬度、背景服務通訊等多個問題，提升整體穩定性與用戶體驗。

### 重點
- claude agents --json 新增 waitingFor 欄位，顯示會話阻擋原因
- 修復 Windows 路徑識別問題：反斜線 (~\、\\server\share) 與大小寫變體現在正確匹配權限規則
- MCP 子 1000ms 逾時設定現改為忽略，回退到預設值，修復全量工具呼叫被中止的問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.162)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 claude agents --json now includes waitingFor showing what a waiting session is blocked on (e.g. permission prompt) 
 --tools : explicitly listing Grep/Glob now provides the dedicated search tools on native builds with embedded search (previously these names were silently ignored) 
 /effort now confirms when your chosen level will persist as the default for new sessions 
 Clicking a slash command in the autocomplete menu now fills it into your prompt instead of running it immediately; press Enter to run 
 Remote Control now shows as a persistent footer pill (with a link to the session) instead of a startup message 
 Renamed Windsurf to Devin Desktop in the /ide menu, /terminal-setup , and /scroll-speed , following the editor's rebrand 
 Fixed a silent startup hang when the config directory is read-only or unwritable — Claude Code now starts with in-memory config and surfaces startup errors instead of showing a blank screen 
 Fixed WebFetch permission rules not being applied to built-in preapproved domains; explicit WebFetch(domain:...) deny/ask/allow rules now take precedence over the preapproved-host auto-allow 
 Fixed Windows permission rules never matching when spelled with backslashes ( ~\ , \\server\share ) or case-variant paths, and Read deny rules not hiding files from Glob/Grep results 
 Fixed an interrupt (Esc) sent at the very start of a turn being silently dropped in stream-json/SDK sessions, leaving the turn running with no "Interrupted" feedback 
 Fixed API 400 no low surrogate in string errors for classifier side-queries and MCP server descriptions containing emoji near a truncation boundary 
 Fixed MCP per-server timeout config values below 1000 ms being floored to a 1-second watchdog that aborted every tool call; sub-1000 ms values are now ignored (falling back to MCP_TOOL_TIMEOUT or default), and claude mcp get annotates them accordingly 
 Fixed the LSP tool's workspaceSymbol operation returning no results; it now accepts a query parameter and passes it to the language server 
 Fixed claude agents cutting live status text (tool args, replies, prompts, exec output) at 60–120 columns on wide terminals; the status detail now uses the full terminal width 
 Fixed claude agents truncating long session names at 40 columns; the name column now grows with terminal width 
 Fixed claude agents attach occasionally bouncing straight back to the session list on the first try after a background-service restart 
 Fixed claude agents Ctrl+V image paste doing nothing in the dispatch input and the session reply box; pasting with no image now shows a hint 
 Fixed backgrounding a session with ← silently losing the conversation when the background service cannot start; the session stays in the list as a failed row you can wake with Enter 
 Fixed replies from the agents view that fail to send being lost; they are now queued for delivery on the next session start 
 Fixed cross-session messaging ( SendMessage ) silently breaking when CLAUDE_CODE_TMPDIR or $TMPDIR points at a deep directory 
 Fixed opening a running background session from claude agents stalling for 5 seconds before attaching 
 Quieter startup: notices group by severity, and session info and announcements share a single line per launch 
 Startup warnings rewritten to be shorter and clearer, each with a concrete fix 
 Launch-prompt warnings (deep link/pre-filled prompt) now stay pinned below the input until you act instead of scrolling away 
 Failed turns now show a compact warning line instead of a multi-line red error block 
 Improved background service startup and claude update verification to wait out endpoint-security scanning of new binaries instead of failing after 5 seconds 
 Background dispatch spawn failures now report the error class name when no errno is available 
 Removed the "Claude in Chrome enabled" and "marketplace installed" startup messages; model auto-updates and the team-onboarding tip now show as quiet notices under the logo

</details>