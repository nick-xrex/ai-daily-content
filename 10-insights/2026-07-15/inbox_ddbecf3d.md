---
id: inbox_ddbecf3d
date: 2026-07-15
source_ref: "[[00-inbox/2026-07-15/0146-claude-code-releases-v2-1-211-ccb3]]"
title: "v2.1.211"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.211
source: claude-code-releases
published_at: 2026-07-15T23:02:35+00:00
fetched_at: 2026-07-16T01:51:59.275408+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 發布 v2.1.211 維護版本，包含 50+ 項修復和改進。新增 --forward-subagent-text flag 和環境變數以在 stream-json 輸出中包含 subagent 文本和思考過程。修復了權限預覽中的字元顯示問題（雙向覆蓋、零寬度和相似引號字元），禁用自動模式對 PreToolUse hook 的覆蓋，並行 session 登出問題，MCP server 空閒後的重連，以及 Vertex/Bedrock 模型設定問題。其他修復涵蓋 subagent 模型覆蓋恢復、.claude/rules 載入、檔案上傳驗證、以及多個 UI 和後臺 session 管理問題。同時修復了 Bedrock/Vertex/Mantle/Foundry 的 prompt caching 計費迴歸。"
key_points:
  - "新增 `--forward-subagent-text` flag 和環境變數以在 stream-json 輸出中包含 subagent 思考內容"
  - "修復權限預覽的字元中和問題（雙向覆蓋/零寬度/相似引號），防止工具輸入視覺上改變批准訊息"
  - "修復並行 session 喚醒時集體登出、MCP server 空閒後重連失敗、Bedrock/Vertex prompt caching 計費迴歸等關鍵問題"
tags: [claude-code, release, bugfix, mcp, security]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.211

Claude Code 發布 v2.1.211 維護版本，包含 50+ 項修復和改進。新增 --forward-subagent-text flag 和環境變數以在 stream-json 輸出中包含 subagent 文本和思考過程。修復了權限預覽中的字元顯示問題（雙向覆蓋、零寬度和相似引號字元），禁用自動模式對 PreToolUse hook 的覆蓋，並行 session 登出問題，MCP server 空閒後的重連，以及 Vertex/Bedrock 模型設定問題。其他修復涵蓋 subagent 模型覆蓋恢復、.claude/rules 載入、檔案上傳驗證、以及多個 UI 和後臺 session 管理問題。同時修復了 Bedrock/Vertex/Mantle/Foundry 的 prompt caching 計費迴歸。

### 重點
- 新增 `--forward-subagent-text` flag 和環境變數以在 stream-json 輸出中包含 subagent 思考內容
- 修復權限預覽的字元中和問題（雙向覆蓋/零寬度/相似引號），防止工具輸入視覺上改變批准訊息
- 修復並行 session 喚醒時集體登出、MCP server 空閒後重連失敗、Bedrock/Vertex prompt caching 計費迴歸等關鍵問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.211)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added --forward-subagent-text flag and CLAUDE_CODE_FORWARD_SUBAGENT_TEXT environment variable to include subagent text and thinking in stream-json output 
 Fixed permission previews relayed to chat channels not neutralizing bidirectional-override, zero-width, and look-alike quote characters, so tool inputs cannot visually alter the approval message 
 Fixed auto mode overriding a PreToolUse hook's ask decision for unsandboxed Bash — a hook ask now floors the decision at a prompt 
 Fixed parallel Claude Code sessions all logging out simultaneously after wake-from-sleep when many sessions share one credential store 
 Fixed plugin MCP servers not reconnecting after an idle web session woke, leaving MCP calls failing until the next message 
 Fixed Claude Code on Vertex and Bedrock attempting the default Opus model at startup and printing a spurious fallback notice when a model is explicitly configured 
 Fixed subagents spawned with an explicit model override reverting to the parent's model when resumed or sent a follow-up message 
 Fixed nested .claude/rules/*.md files loading even when setting sources exclude project settings 
 Fixed file upload validation: filenames ending in a DOS device suffix ( .prn ) or trailing dot are now accepted, and files with multiple hard links are refused 
 Fixed file uploads to Claude in Chrome from remote and CLI sessions 
 Fixed edits that leave the input as "?" being silently swallowed and toggling the shortcuts panel 
 Fixed a startup hang when the Claude in Chrome extension is enabled but Chrome is not running 
 Fixed a 300ms delay revealing async content (Settings tabs, Stats, diff views, and other loading states) 
 Fixed reopening a just-stopped background session from the agents view starting a blank conversation under the same session id 
 Fixed /loop hiding the session from /resume after a single use 
 Fixed screen reader users losing the audible terminal bell after /terminal-setup or onboarding terminal setup 
 Fixed background jobs on LLM gateway auth ( ANTHROPIC_AUTH_TOKEN + ANTHROPIC_BASE_URL ) coming back "Not logged in" after the daemon respawns them 
 Fixed claude agents jobs becoming permanently undeletable when git no longer recognizes their worktree — the row now shows why the delete was refused instead of silently reappearing 
 Fixed /clear not resetting the session cost counter — the statusline's cost now starts at $0 after /clear 
 Fixed Claude in Chrome setup pages failing to open in the browser on Windows 
 Fixed headless print-mode sessions on Windows crashing or silently exiting when stdin is unreadable 
 Fixed background session titles in the agents view showing the naming model's refusal text when the prompt contains a link 
 Fixed background agents killed by the user auto-respawning, and revived agents re-running stale prompts from old sessions 
 Fixed routines with no schedule reporting a next run time in the year 1 
 Hardened synced skill/plugin directory naming on Windows and kept CCR web fetch/search proxies working after /clear 
 Improved terminal layout and rendering performance 
 Improved background agent result reporting — Claude now reports the status of still-running agents and waits for the real completion instead of fabricating results 
 Improved the memory index over-limit warning to measure only loaded content, excluding frontmatter and HTML comments 
 Updated integer environment variables (timeouts, token budgets, retry counts) to accept scientific notation and digit-separator spellings like 1e6 and 64_000 
 Updated documentation links to the current docs sites 
 Changed "always allow" permission rules to save at the repository root, so approvals granted in a git worktree persist across sessions and worktrees 
 Changed /usage-credits to ask for confirmation before sending a request to organization admins 
 Changed Vim mode s and S (substitute char/line) to work in NORMAL mode, matching vim behavior 
 [VSCode] Updated the Remote Control banner to describe what it does 
 Claude in Chrome: hardened file-upload path validation 
 Claude in Chrome: save_to_disk on screenshot actions now writes the image to disk and returns the path; previously it did nothing 
 Fixed a prompt-caching regression on Bedrock, Vertex, Mantle, and Foundry that billed the trailing system context block as fresh input tokens on every request.

</details>