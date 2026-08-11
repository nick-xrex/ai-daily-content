---
id: inbox_02a6620f
date: 2026-08-08
source_ref: "[[00-inbox/2026-08-08/2221-claude-code-releases-v2-1-225-6385]]"
title: "v2.1.225"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.225
source: claude-code-releases
published_at: 2026-08-08T01:09:26+00:00
fetched_at: 2026-08-08T23:55:54.493544+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.225 發布重大更新，新增 gateway 花費上限警告（顯示上限值、重設時間、營運商訊息）、workspace 不信任目錄提示機制；修復 10+ 項穩定性與安全問題，包括 OAuth token 401 錯誤、macOS MCP 伺服器間歇性認證失敗、auto mode 誤計安全拒絕觸發重試循環、headless session 訊息滯留、Remote Control 會話恢復後對話歷史損壞、VSCode Focus view 摺疊遺漏、SendMessage 可按名稱啟動 Remote Control 會話。"
key_points:
  - "Gateway spend-limit warning：顯示花費上限、重設時間及營運商警告訊息（配合 gateway 2.1.225）"
  - "Workspace trust prompt：針對不信任目錄加入信任確認提示，與 Claude app 行為一致"
  - "關鍵修復：OAuth token 替換的 401 錯誤（headless session 中斷）、macOS MCP OAuth 伺服器間歇性失敗、auto mode 安全拒絕誤計導致無限重試、Remote Control 會話跨機器訊息處理"
tags: [claude-code, security, oauth, auto-mode, remote-control]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.225

Claude Code v2.1.225 發布重大更新，新增 gateway 花費上限警告（顯示上限值、重設時間、營運商訊息）、workspace 不信任目錄提示機制；修復 10+ 項穩定性與安全問題，包括 OAuth token 401 錯誤、macOS MCP 伺服器間歇性認證失敗、auto mode 誤計安全拒絕觸發重試循環、headless session 訊息滯留、Remote Control 會話恢復後對話歷史損壞、VSCode Focus view 摺疊遺漏、SendMessage 可按名稱啟動 Remote Control 會話。

### 重點
- Gateway spend-limit warning：顯示花費上限、重設時間及營運商警告訊息（配合 gateway 2.1.225）
- Workspace trust prompt：針對不信任目錄加入信任確認提示，與 Claude app 行為一致
- 關鍵修復：OAuth token 替換的 401 錯誤（headless session 中斷）、macOS MCP OAuth 伺服器間歇性失敗、auto mode 安全拒絕誤計導致無限重試、Remote Control 會話跨機器訊息處理

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.225)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added gateway spend-limit support to Claude Code's usage warning; the limit-reached message now names the cap, its reset time, and the operator's message (requires the gateway on 2.1.225) 
 Added a workspace trust prompt to claude agents for untrusted directories, matching the behavior of claude 
 Fixed a transient 401 replacing a long-lived CLAUDE_CODE_OAUTH_TOKEN with a stored login's short-lived token, breaking headless sessions until restart 
 Fixed MCP OAuth servers on macOS intermittently failing with a burst of 401 errors, as if never authenticated, after a keychain read timed out 
 Fixed auto mode counting a safety-filter refusal of its own permission check toward the consecutive-block limit; the action is still denied, but the model is now told to move on rather than retry 
 Fixed cross-session messages staying parked without a notice or expiry in headless sessions and during startup 
 Fixed conversation history breaking on Remote Control session resume after very large conversations were compacted 
 Fixed hovering over a session in another project in the agents list changing the directory the next agent starts in 
 Fixed claude self-hosted-runner registering and then failing every session when --base-dir cannot be created or written; it now exits at startup with a clear error 
 Fixed Claude Code on the web sessions being misreported as stuck, re-sending a growing event backlog on every reconnect 
 Improved Remote Control: photos attached from the Claude app are now shown to Claude directly instead of being read from disk with a separate tool call 
 [VSCode] Fixed Focus view folding away the latest to-do list, a pending question's context, and settled answers; thinking-only folds show "Thought for Ns" and re-collapse when their turn completes 
 SendMessage can now start a conversation with your Remote Control sessions on other machines by name ( ListAgents shows them as name [ref] ), instead of only replying after they message you first 
 SendMessage: a Remote Control recipient you already confirmed is never swapped for a same-named session on this machine when its own list couldn't be checked

</details>