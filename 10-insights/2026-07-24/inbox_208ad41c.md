---
id: inbox_208ad41c
date: 2026-07-24
source_ref: "[[00-inbox/2026-07-24/0122-claude-code-releases-v2-1-219-2b2a]]"
title: "v2.1.219"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.219
source: claude-code-releases
published_at: 2026-07-24T17:14:23+00:00
fetched_at: 2026-07-27T01:26:39.620652+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.219 推出 Claude Opus 5 為新預設 Opus 模型，支援 1M 上下文，Fast Mode 定價 $10/$50 per Mtok。新增 sandbox.network.strictAllowlist 控制沙箱命令網絡存取、DirectoryAdded hook 支援中途動態註冊工作目錄、MCP 伺服器錯誤報告等。修正 20+ 個邊界案例：流式 API 錯誤後答案遺失、Remote Control 快速模式狀態過時、Vim mode 鍵盤互動、螢幕閱讀器回音、GNU screen 複製等。Subagents 嵌套深度提升至 3（預設上限，可設 CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH=1 禁用）。Opus 4.7 已從 Fast Mode 移除。"
key_points:
  - "Claude Opus 5 新模型上線：1M context，Fast Mode $10/$50 per Mtok"
  - "新增 sandbox.network.strictAllowlist 和 DirectoryAdded hook，強化安全與動態配置管理"
  - "Subagents 嵌套深度由 1 升至 3，20+ 可靠性修復（流式錯誤、Vim mode、螢幕閱讀器等）"
tags: [claude-code, opus-5, model-release, security-sandbox, subagent-depth, reliability-fixes]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.219

Claude Code v2.1.219 推出 Claude Opus 5 為新預設 Opus 模型，支援 1M 上下文，Fast Mode 定價 $10/$50 per Mtok。新增 sandbox.network.strictAllowlist 控制沙箱命令網絡存取、DirectoryAdded hook 支援中途動態註冊工作目錄、MCP 伺服器錯誤報告等。修正 20+ 個邊界案例：流式 API 錯誤後答案遺失、Remote Control 快速模式狀態過時、Vim mode 鍵盤互動、螢幕閱讀器回音、GNU screen 複製等。Subagents 嵌套深度提升至 3（預設上限，可設 CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH=1 禁用）。Opus 4.7 已從 Fast Mode 移除。

### 重點
- Claude Opus 5 新模型上線：1M context，Fast Mode $10/$50 per Mtok
- 新增 sandbox.network.strictAllowlist 和 DirectoryAdded hook，強化安全與動態配置管理
- Subagents 嵌套深度由 1 升至 3，20+ 可靠性修復（流式錯誤、Vim mode、螢幕閱讀器等）

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.219)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added Claude Opus 5 ( claude-opus-5 ), now the default Opus model — 1M context, fast mode at $10/$50 per Mtok 
 Added sandbox.network.strictAllowlist setting to deny non-allowlisted hosts for sandboxed commands without prompting 
 Added DirectoryAdded hook that fires after /add-dir or the SDK register_repo_root control request registers a new working directory mid-session 
 Added mcp_server_errors to the headless stream-json init event, listing --mcp-config entries skipped by config validation; terminal runs print a startup warning 
 Added the workflowSizeGuideline settings key so the advisory Dynamic workflow size guideline can be set from any settings file; the /config row is hidden while one does 
 Added nested subagent forwarding in stream-json: subagents spawned at depth-2+ now appear when --forward-subagent-text is set, keyed by their spawning Agent tool_use id 
 Fixed claude -p text output dropping the answer already produced when a turn dies on a mid-stream API error 
 Added HTTP status and error text to claude mcp list and /mcp when a server fails to connect, and a warning for MCP config values with hidden leading or trailing whitespace 
 Fixed a permission you approved while a self-hosted runner was restarting being dropped when the session resumed, so the approved action now runs 
 Fixed the Fable model row showing "Requires usage credits" for plans that include it, when a stale cache had baked the label in 
 Fixed a SIGTERM arriving while a self-hosted runner was starting up leaving a stale active row until the lease expired; it now deregisters cleanly 
 Added structured failure categories to self-hosted runner spawn and session failures, so hook errors, runner crashes and config errors can be told apart 
 Fixed the /model picker showing the merged Opus row as plain "Opus" instead of "Opus (1M context)" 
 Fixed copy-on-select inside GNU screen printing base64 into the terminal instead of copying the selection 
 Fixed Remote Control clients keeping a stale fast-mode status after a model switch, reconnect, or failed org check 
 Fixed CLAUDE_CODE_GIT_BASH_PATH on Windows exiting or being used as bash when the path isn't a bash/sh binary; it's now ignored with a warning 
 Fixed Vim mode: pressing ← on an empty prompt now returns to the agent view from NORMAL mode, not just INSERT 
 Fixed screen-reader mode rewriting the entire input line on every keystroke instead of echoing only the typed character 
 Improved the "Remote Control is only available via api.anthropic.com" error to name the specific setting that caused it 
 Improved claude --teleport to show which repo your current checkout points at when it doesn't match the session's repo 
 Changed dynamic workflows to default to a medium size guideline (aim for fewer than 15 agents); pick another size or unrestricted with Dynamic workflow size in /config 
 Changed managed MCP allowlist/denylist ${VAR} entries to resolve from the startup environment and managed-settings env instead of settings-file env 
 Changed the /model picker to highlight only the newest model's name, so the highlight marks the new release rather than an arbitrary subset of the list 
 Added the current default workflow size to the running-workflow status line, with a pointer to /config for changing it 
 Removed Opus 4.7 from fast mode; /fast now applies to Opus 5 and Opus 4.8 
 Updated the claude-api skill to default to Claude Opus 5, with a migration path from Opus 4.8 
 Subagents can now spawn nested subagents up to depth 3 by default (was 1); set CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH=1 to disable nesting

</details>