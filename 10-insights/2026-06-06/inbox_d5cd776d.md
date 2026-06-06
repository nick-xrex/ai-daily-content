---
id: inbox_d5cd776d
date: 2026-06-06
source_ref: "[[00-inbox/2026-06-06/0215-claude-code-releases-v2-1-166-0240]]"
title: "v2.1.166"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.166
source: claude-code-releases
published_at: 2026-06-06T00:55:18+00:00
fetched_at: 2026-06-06T02:20:47.091167+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.166 推出多項功能和修復。新增 fallbackModel 設定可在主模型過載時自動切換至最多三個後備模型；加強跨工作階段訊息傳遞安全性，禁止權限濫用；MAX_THINKING_TOKENS=0 可禁用預設思考功能；修復 25+ 個 bug，涵蓋 JetBrains IDE 終端閃爍、Kitty 鍵盤協議按鍵遺失、PowerShell 命令驗證逾時、遠端工作階段卡頓、macOS 背景程序無限迴圈、git worktree 當機等。"
key_points:
  - "新增 fallbackModel 設定，API 過載時自動循環嘗試最多三個後備模型，提升服務可用性"
  - "強化跨工作階段訊息安全：中繼訊息不再攜帶使用者權限，拒絕權限請求濫用"
  - "修復 25+ 個 bug，包括終端相容性、遠端工作階段、git worktree 整合、思考功能等"
tags: [claude-code, fallback-model, reliability, security-hardening, bug-fix]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.166

Claude Code v2.1.166 推出多項功能和修復。新增 fallbackModel 設定可在主模型過載時自動切換至最多三個後備模型；加強跨工作階段訊息傳遞安全性，禁止權限濫用；MAX_THINKING_TOKENS=0 可禁用預設思考功能；修復 25+ 個 bug，涵蓋 JetBrains IDE 終端閃爍、Kitty 鍵盤協議按鍵遺失、PowerShell 命令驗證逾時、遠端工作階段卡頓、macOS 背景程序無限迴圈、git worktree 當機等。

### 重點
- 新增 fallbackModel 設定，API 過載時自動循環嘗試最多三個後備模型，提升服務可用性
- 強化跨工作階段訊息安全：中繼訊息不再攜帶使用者權限，拒絕權限請求濫用
- 修復 25+ 個 bug，包括終端相容性、遠端工作階段、git worktree 整合、思考功能等

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.166)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added fallbackModel setting to configure up to three fallback models tried in order when the primary model is overloaded or unavailable; --fallback-model now also applies to interactive sessions 
 Added glob pattern support in deny rule tool-name position ( "*" denies all tools); allow rules reject non-MCP globs, and unknown tool names in deny rules warn at startup 
 Hardened cross-session messaging: messages relayed via SendMessage from other Claude sessions no longer carry user authority — receivers refuse relayed permission requests, and auto mode blocks them 
 MAX_THINKING_TOKENS=0 , --thinking disabled , and the per-model thinking toggle now disable thinking on models that think by default via the Claude API (3P providers unchanged) 
 Claude Code now retries a turn once on the fallback model when the API rejects an unexpected non-retryable error; auth, rate-limit, request-size, and transport errors still surface immediately 
 claude update now announces the target version before downloading instead of going silent 
 claude agents : typing a URL into the list now filters to the session whose first prompt contained it 
 Fixed a recurring "image could not be processed" error and extra token usage when an unprocessable image was sent in a session 
 Fixed remote sessions becoming permanently stuck when a brief backend disruption occurred during worker registration at startup 
 Fixed flickering in JetBrains IDE terminals (IntelliJ, PyCharm, WebStorm, etc.) on 2026.1+ by enabling synchronized output 
 Fixed Shift+non-ASCII characters (e.g. Shift+ä → Ä) being dropped in terminals using the Kitty keyboard protocol (WezTerm, Ghostty, kitty) 
 Fixed PowerShell command validation occasionally hanging far past its time budget on Windows when a killed process's children held its output pipes 
 Fixed orphaned claude --bg-pty-host processes spinning at 100% CPU after the daemon dies while connected on macOS 
 Fixed voice mode requiring /login to clear a stale auth check after toggling /voice 
 Fixed managed settings with an invalid entry silently disabling enforcement of their remaining valid policies 
 Fixed managed-settings allowedMcpServers / deniedMcpServers predicates not matching when they use ${VAR} references 
 Fixed background agent sessions that entered a git worktree crash-looping with "No conversation found" when reopened from claude agents 
 Fixed duplicated thinking text in the Ctrl+O transcript view while streaming 
 Fixed /doctor showing a contradictory failed "Not inside a remote session" check when run inside a remote session 
 Fixed the cursor sticking at the end of the first line when typing a multiline prompt in the claude agents dispatch and reply inputs 
 Fixed blank lines appearing between background agent rows in the task list on terminals without Unicode support

</details>