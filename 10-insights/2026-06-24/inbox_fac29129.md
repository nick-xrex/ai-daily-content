---
id: inbox_fac29129
date: 2026-06-24
source_ref: "[[00-inbox/2026-06-24/2200-claude-code-releases-v2-1-191-48c2]]"
title: "v2.1.191"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.191
source: claude-code-releases
published_at: 2026-06-24T21:58:12+00:00
fetched_at: 2026-06-24T22:04:38.478158+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 編輯器發布 v2.1.191，包含多項改進和修復。新增 /rewind 功能支持從 /clear 前的狀態恢復對話。修復了 UI 滾動跳動、後台代理行為、權限管理等問題。改進 MCP 伺服器可靠性，能力發現與 OAuth 認證流程現包含短退避重試機制應對瞬時網絡錯誤；無頭環境直接跳轉 URL 粘貼提示無需瀏覽器彈窗。通過合併文本更新至 100ms 間隔減少流式響應時 CPU 使用約 37%，優化終端輸出緩存以減少長會話記憶體增長。"
key_points:
  - "新增 /rewind 功能從 /clear 前恢復對話歷史"
  - "MCP 伺服器能力發現（tools/list、prompts/list、resources/list）新增重試機制，OAuth 認證改進無頭環境流程"
  - "流式響應期間 CPU 使用減少 ~37%（文本更新合併至 100ms）；終端輸出緩存優化減少長會話記憶體增長"
tags: [claude-code, performance-optimization, mcp-reliability, ui-fixes, dev-tools]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.191

Claude Code 編輯器發布 v2.1.191，包含多項改進和修復。新增 /rewind 功能支持從 /clear 前的狀態恢復對話。修復了 UI 滾動跳動、後台代理行為、權限管理等問題。改進 MCP 伺服器可靠性，能力發現與 OAuth 認證流程現包含短退避重試機制應對瞬時網絡錯誤；無頭環境直接跳轉 URL 粘貼提示無需瀏覽器彈窗。通過合併文本更新至 100ms 間隔減少流式響應時 CPU 使用約 37%，優化終端輸出緩存以減少長會話記憶體增長。

### 重點
- 新增 /rewind 功能從 /clear 前恢復對話歷史
- MCP 伺服器能力發現（tools/list、prompts/list、resources/list）新增重試機制，OAuth 認證改進無頭環境流程
- 流式響應期間 CPU 使用減少 ~37%（文本更新合併至 100ms）；終端輸出緩存優化減少長會話記憶體增長

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.191)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added /rewind support for resuming a conversation from before /clear was run 
 Fixed scroll position jumping to the bottom while reading earlier output during a streaming response 
 Fixed background agents resurrecting after being stopped — stopping an agent from the tasks panel is now permanent 
 Fixed /voice showing a generic "not available" message when disabled by an organization's policy — it now explains the restriction 
 Fixed /login URL opening truncated in Windows Terminal when it wraps across lines 
 Fixed Cmd+click on links in fullscreen mode for Ghostty over ssh/tmux 
 Fixed claude agents sending builtin slash commands like /usage to background sessions as prompt text instead of showing a hint 
 Fixed claude agents job rows showing full filesystem paths for pasted images instead of the [Image #N] placeholder 
 Fixed hooks with comma-separated matchers (e.g. "Bash,PowerShell" ) silently never firing 
 Fixed /permissions Recently-denied tab: approving a denial now persists on close instead of being silently discarded 
 Fixed the agent panel jumping by one row when scrolling the roster past the overflow cap 
 Fixed the welcome splash art overflowing the default 80×24 macOS Terminal window 
 Fixed managed settings: forceRemoteSettingsRefresh now takes effect when set via MDM or file policy, and the fetch sends Cache-Control: no-cache to prevent proxies from serving stale responses 
 Improved sandbox network permission dialog: hosts you allow with "Yes" are now remembered for the rest of the session instead of re-prompting on every connection 
 Improved MCP server reliability: capability discovery ( tools/list , prompts/list , resources/list ) now retries transient network errors with short backoff 
 Improved MCP OAuth: discovery and token requests now retry once after transient network errors, and headless environments skip the browser popup and go straight to the paste-the-URL prompt 
 Improved MCP error messages: HTTP 404 errors now show the URL and point to your MCP config 
 Improved vim mode prompt-history search (NORMAL / ) to hint how to reach slash commands 
 Reduced CPU usage during streaming responses by ~37% by coalescing text updates to 100ms 
 Reduced long-session memory growth from terminal output cache

</details>