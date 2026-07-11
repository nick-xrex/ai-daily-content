---
id: inbox_ee0952e0
date: 2026-07-10
source_ref: "[[00-inbox/.../inbox_ee0952e0]]"
title: "v2.1.206"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.206
source: claude-code-releases
published_at: 2026-07-10T01:45:26+00:00
fetched_at: 2026-07-11T01:54:18.500453+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.206 發布了 43 項改進，核心包括背景 agent 自動升級（新版本發布後立即在背景更新，避免 stale session 延遲）、MCP 伺服器 per-server request_timeout_ms 修復（長執行任務不再因 60s 預設逾時而失敗）、CLAUDE_CODE_EXTRA_BODY 環變數傳播修復（背景 worker 現正確遵循 dispatcher session）、OAuth MCP 自動重新認證修復、以及模型選擇器、/cd 路徑建議、/doctor 檢查、/commit-push-pr 自動 origin 推送等 UX 改進。此版本著重穩定性與 MCP 整合品質。"
key_points:
  - "背景 agent 自動升級：新版本發布後立即背景升級，消除 stale session 升級延遲瓶頸"
  - "MCP per-server timeout 修復：request_timeout_ms 配置現已正確生效，60s 預設逾時問題解決"
  - "環變數傳播修復：CLAUDE_CODE_EXTRA_BODY 與其他環變現遵循 dispatcher session，背景 worker 完整繼承"
tags: [claude-code, mcp, background-agents, bug-fixes]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.206

Claude Code v2.1.206 發布了 43 項改進，核心包括背景 agent 自動升級（新版本發布後立即在背景更新，避免 stale session 延遲）、MCP 伺服器 per-server request_timeout_ms 修復（長執行任務不再因 60s 預設逾時而失敗）、CLAUDE_CODE_EXTRA_BODY 環變數傳播修復（背景 worker 現正確遵循 dispatcher session）、OAuth MCP 自動重新認證修復、以及模型選擇器、/cd 路徑建議、/doctor 檢查、/commit-push-pr 自動 origin 推送等 UX 改進。此版本著重穩定性與 MCP 整合品質。

### 重點
- 背景 agent 自動升級：新版本發布後立即背景升級，消除 stale session 升級延遲瓶頸
- MCP per-server timeout 修復：request_timeout_ms 配置現已正確生效，60s 預設逾時問題解決
- 環變數傳播修復：CLAUDE_CODE_EXTRA_BODY 與其他環變現遵循 dispatcher session，背景 worker 完整繼承

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.206)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.206

What's changed 
 
 Added directory path suggestions to /cd , matching /add-dir behavior 
 Added a /doctor check that proposes trimming checked-in CLAUDE.md files by cutting content Claude could derive from the codebase 
 /commit-push-pr now auto-allows git push to the repo's configured push remote ( remote.pushDefault , or the sole remote when only one is configured) in addition to origin 
 Gateway: /login now supports Anthropic-operated public gateway endpoints 
 EnterWorktree now asks for confirmation before entering a git worktree outside the project's .claude/worktrees/ directory 
 Background agents now upgrade to a new version in the background right after a Claude Code update, instead of paying a slow stale-session upgrade when you attach 
 Fixed an expired login failing every model with a misleading "There's an issue with the selected model" error instead of prompting to run /login 
 Fixed claude --resume and --continue not responding to keyboard input on startup 
 Fixed MCP servers configured via --mcp-config or .mcp.json ignoring a per-server request_timeout_ms , which caused long-running MCP tool calls to time out at the 60s default in fresh sessions 
 Fixed CLAUDE_CODE_EXTRA_BODY being silently ignored by claude agents / --bg background workers; the shell-exported override now follows the dispatching session 
 Fixed OAuth MCP servers requiring manual re-authentication after a single failed token refresh 
 Fixed --permission-prompt-tool pointing at an MCP server crashing with "MCP tool not found" on cold start before the server finishes connecting 
 Fixed /model picker rows printing a price for a different model than the row named, and stopped quoting first-party list prices on providers that don't bill them 
 Fixed server-provided model rows being misplaced in the /model picker when an entitlement or allowlist restriction drops the row they were positioned against 
 Fixed desktop sessions getting stuck showing "running" after a slash command was sent mid-turn 
 Fixed keyboard input being ignored in the agents view when a setup prompt appeared before a bare claude --resume on Windows 
 Fixed claude rm leaving the removed job in the daemon roster, causing the row to reappear in claude agents 
 Fixed /remote-control showing "Unknown command" when logged out — it now explains how to sign in 
 Fixed left arrow not stepping back out of a phase or agent in the workflow detail view 
 Fixed /status listing the same broken-install warning twice 
 Fixed false "disused plugin" tips and skewed disuse telemetry for LSP plugins 
 Fixed /doctor 's update check to compare Homebrew installs against their cask's channel instead of the settings channel 
 Fixed the fullscreen jump-to-bottom pill suggesting Ctrl+End on macOS, not showing rebound chords, and wrapping over the transcript 
 Bedrock: fixed a multi-minute startup hang when using an awsCredentialExport helper on networks with restricted egress 
 Improved /code-review findings quality on claude-opus-4-8 across all effort levels 
 Improved agents view: status column now uses full terminal width instead of truncating at 64 characters 
 Changed agents view: Ctrl+X now permanently removes a completed session, and sessions no longer render twice; deleted background jobs stay deleted

</details>