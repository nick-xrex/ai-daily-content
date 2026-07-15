---
id: inbox_ef1a85c1
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/0011-claude-code-releases-v2-1-210-0727]]"
title: "v2.1.210"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.210
source: claude-code-releases
published_at: 2026-07-14T23:45:25+00:00
fetched_at: 2026-07-15T00:16:29.391042+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.210 版本發布，聚焦於隔離性、安全性和穩定性修復。最關鍵的修復是 worktree subagents 隔離漏洞—此前 subagents 能對主倉庫運行 git-mutating 命令，現已限制在各自的 worktree 內。第二個重要安全修復是 ultracode keyword opt-in 在非人工輸入（webhook payload、中繼 PR 評論）時誤觸發，已予修正。穩定性方面修復了多個導致 session crash 的問題：工具返回 bigint 或純文本而非 UI 元素時 crash、hook callback timeout 被誤報為用戶拒絕導致自動化停止等。此外修復了 plugin MCP servers 在重新同步時被意外刪除、paste markers 洩漏至外部編輯器等 UI 細節 bug。改進方面新增 elapsed-time counter 提示長運行工具調用進度，permission mode 分類器預設升級至 Sonnet 5。"
key_points:
  - "修復 worktree subagents 隔離漏洞—防止向主倉庫運行 git-mutating 命令，確保隔離工作樹獨立性"
  - "修復 ultracode keyword opt-in 在 webhook/PR 評論等非人工輸入時誤觸發，提高自動化工作流可控性"
  - "修復多個 session crash 問題（工具返回 bigint/純文本、hook timeout 誤報為拒絕）及 MCP servers 意外刪除，提升穩定性"
tags: [claude-code, isolation-security, bug-fixes, ultracode, stability]
topics: [foundation_models.claude]
importance: 4
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.210

Claude Code v2.1.210 版本發布，聚焦於隔離性、安全性和穩定性修復。最關鍵的修復是 worktree subagents 隔離漏洞—此前 subagents 能對主倉庫運行 git-mutating 命令，現已限制在各自的 worktree 內。第二個重要安全修復是 ultracode keyword opt-in 在非人工輸入（webhook payload、中繼 PR 評論）時誤觸發，已予修正。穩定性方面修復了多個導致 session crash 的問題：工具返回 bigint 或純文本而非 UI 元素時 crash、hook callback timeout 被誤報為用戶拒絕導致自動化停止等。此外修復了 plugin MCP servers 在重新同步時被意外刪除、paste markers 洩漏至外部編輯器等 UI 細節 bug。改進方面新增 elapsed-time counter 提示長運行工具調用進度，permission mode 分類器預設升級至 Sonnet 5。

### 重點
- 修復 worktree subagents 隔離漏洞—防止向主倉庫運行 git-mutating 命令，確保隔離工作樹獨立性
- 修復 ultracode keyword opt-in 在 webhook/PR 評論等非人工輸入時誤觸發，提高自動化工作流可控性
- 修復多個 session crash 問題（工具返回 bigint/純文本、hook timeout 誤報為拒絕）及 MCP servers 意外刪除，提升穩定性

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.210)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added a live elapsed-time counter to the collapsed tool summary line so long-running tool calls visibly tick instead of looking stuck 
 Added a startup warning for Write(path) , NotebookEdit(path) , and Glob(path) permission rules — use Edit(path) or Read(path) instead 
 Fixed isolation: 'worktree' subagents being able to run git-mutating commands against the main repo checkout instead of their own isolated worktree 
 Fixed the ultracode keyword opt-in firing on non-human-originated input such as webhook payloads and relayed PR comments 
 Fixed a rendered text fragment leaking into crash telemetry when a UI component returned content outside a styled text element 
 Fixed paste markers leaking into external editors opened from Claude Code, which could appear as stray È/É characters around pasted text 
 Fixed claude attach sometimes failing with "job not found" or "agent is still starting" errors during session transitions — attach now waits for the daemon to settle, and terminal resizes during a slow attach are applied once it completes 
 Fixed a session crash when a tool's result renderer returned a numeric bigint value or plain text instead of a UI element 
 Fixed a hook callback timeout being misreported to the model as a user rejection, which made unattended sessions stop and wait 
 Fixed Claude assuming a cd took effect after its command was moved to the background; the tool result now states the working directory is unchanged 
 Fixed plugin-provided MCP servers being torn down when MCP servers are re-synced mid-session 
 Fixed plan approvals without edits being labeled "(edited by user)" and overwriting the plan file with a stale snapshot 
 Fixed /doctor skipping its auto-mode-default proposal on Bedrock, Vertex, and Foundry, where auto mode no longer needs an opt-in 
 Fixed Grep content mode claiming "No matches found" when paginating past the end of results 
 Fixed unmatched $1 / $2 positional placeholders in skills and commands being silently stripped; they are now preserved verbatim 
 Fixed plugin cache writes leaving temp files behind on failure and failing on locked-file renames on Windows and network filesystems 
 Fixed background workers crash-looping when a client resets its connection to the background service 
 Fixed claude agents --effort ultracode not reaching dispatched sessions; the value was silently dropped 
 Fixed pressing ← to open the agents view dropping the task tracker when returning to the session 
 Fixed the agents dashboard retaining pasted images from abandoned reply drafts after their session was deleted 
 Fixed killed background sessions leaving a permanent git worktree lock behind; the periodic sweep now releases locks whose owning process is gone 
 Fixed SDK MCP servers registered via an initialize control request waiting until the next turn to start connecting 
 Fixed returning to the agents view from a session leaving overlapping ghost frames with CLAUDE_CODE_DISABLE_ALTERNATE_SCREEN=1 
 Fixed late-appearing .claude/* symlinks not being reconciled into the sandbox deny-write list 
 Hardened the Agent tool against indirect prompt injection via content a subagent read 
 Improved the Bash/PowerShell tool message when a command hits its timeout and is auto-backgrounded, so the model can distinguish a hang from an explicit background request 
 Improved auto mode: the permission classifier now defaults to Sonnet 5 for external sessions, validated on the session's first request and pinned for the session 
 Improved the bundled dataviz skill's chart color validation with perceptual OKLab color difference and recalibrated color-blindness thresholds 
 Memory writes that leave a MEMORY.md index over its read limit now produce an explicit error instead of silent truncation 
 Screen reader mode now announces permission mode changes aloud when cycling modes with Shift+Tab 
 The agents footer hint now shows how many background agents are waiting on your input, with a brief color emphasis when the count changes 
 Agent view: the session you pressed ← from stays visibly marked even after mouse hover or arrow keys move the selection 
 Fable temporarily shows as unavailable in the advisor picker while a server-side issue causing Fable advisor failures is fixed

</details>