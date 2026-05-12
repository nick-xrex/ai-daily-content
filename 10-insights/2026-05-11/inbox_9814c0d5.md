---
id: inbox_9814c0d5
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/0113-claude-code-releases-v2-1-139-ca64]]"
title: "v2.1.139"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.139
source: claude-code-releases
published_at: 2026-05-11T18:43:42+00:00
fetched_at: 2026-05-12T01:17:36.593401+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 釋出 v2.1.139，引入 agent view（研究預覽）統一管理所有 session，以及 /goal command 讓 Claude 跨轉自動工作直到滿足完成條件，並即時顯示 elapsed/turns/tokens。新增 hook args 支援 string[] 形式直接執行命令無需 shell，plugin details 命令顯示 component inventory 及預估 token 成本。修復了 10+ MCP servers 配置時的 silent exit 1 問題，compaction prompt 現在保留敏感使用者指令，/mcp Reconnect 無需重啟即可讀取 .mcp.json 編輯。版本包含超過 30 項修復，涵蓋 UI 互動、MCP 伺服器穩定性及邊界情況。"
key_points:
  - "Agent view 統一管理所有 session（running/blocked/done）；/goal command 自動跨轉工作，即時顯示 elapsed/turns/tokens 疊層"
  - "Hook args string[] 形式直接執行命令無需 shell；plugin details 顯示 component inventory 及預估 per-session token 成本"
  - "修復 10+ MCP server 配置的 silent exit 1；MCP 伺服器 SSE 響應上限 16 MB/frame；熱重載 symlinked settings.json"
tags: [claude-code, agent-management, development-tooling, mcp-improvements, bug-fixes]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.139

Claude Code 釋出 v2.1.139，引入 agent view（研究預覽）統一管理所有 session，以及 /goal command 讓 Claude 跨轉自動工作直到滿足完成條件，並即時顯示 elapsed/turns/tokens。新增 hook args 支援 string[] 形式直接執行命令無需 shell，plugin details 命令顯示 component inventory 及預估 token 成本。修復了 10+ MCP servers 配置時的 silent exit 1 問題，compaction prompt 現在保留敏感使用者指令，/mcp Reconnect 無需重啟即可讀取 .mcp.json 編輯。版本包含超過 30 項修復，涵蓋 UI 互動、MCP 伺服器穩定性及邊界情況。

### 重點
- Agent view 統一管理所有 session（running/blocked/done）；/goal command 自動跨轉工作，即時顯示 elapsed/turns/tokens 疊層
- Hook args string[] 形式直接執行命令無需 shell；plugin details 顯示 component inventory 及預估 per-session token 成本
- 修復 10+ MCP server 配置的 silent exit 1；MCP 伺服器 SSE 響應上限 16 MB/frame；熱重載 symlinked settings.json

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.139)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added agent view (Research Preview): a single list of every Claude Code session — running, blocked on you, or done. Run claude agents to get started. See https://code.claude.com/docs/en/agent-view 
 Added /goal command: set a completion condition and Claude keeps working across turns until it's met. Works in interactive, -p , and Remote Control. Shows live elapsed/turns/tokens as an overlay panel 
 Added /scroll-speed command to tune mouse wheel scroll speed with a live preview 
 Added claude plugin details &lt;name&gt; to show a plugin's component inventory and projected per-session token cost 
 Added transcript view navigation: ? for keyboard shortcuts, { / } to jump between user prompts, v to toggle shortcut panel 
 Added hook args: string[] field (exec form) that spawns the command directly without a shell, so path placeholders never need quoting 
 Added hook continueOnBlock config option for PostToolUse — set to true to feed the hook's rejection reason back to Claude and continue the turn 
 MCP stdio servers now receive CLAUDE_PROJECT_DIR in their environment, matching hooks. Plugin configs can reference ${CLAUDE_PROJECT_DIR} in commands 
 Compaction prompt now asks the model to preserve sensitive user instructions 
 /mcp Reconnect now picks up .mcp.json edits without a restart, and shows the HTTP status and URL when reconnecting fails 
 /context all per-skill token estimates now account for the model's tokenizer and show rounded values 
 claude plugin install &lt;name&gt;@&lt;marketplace&gt; now auto-refreshes the marketplace and retries before reporting a plugin as not found 
 /plugin installed-plugin details now show hook event names and MCP server names cleanly 
 /context now shows the providing plugin's name for plugin-sourced skills 
 Remote MCP server reconnect retry on transient failures is now enabled for all users 
 API requests from subagents now carry x-claude-code-agent-id / x-claude-code-parent-agent-id headers, and claude_code.llm_request OTEL spans include agent_id / parent_agent_id attributes 
 Remote Control, /schedule , claude.ai MCP connectors, and notification preferences are now disabled when ANTHROPIC_API_KEY / apiKeyHelper / ANTHROPIC_AUTH_TOKEN is set, even if a Claude.ai login also exists. Unset the API key to use these features 
 Fixed a deadlock where expired credentials and the forceRemoteSettingsRefresh policy setting blocked claude auth login / logout / status with no way to recover 
 Fixed autoAllowBashIfSandboxed not auto-approving commands with shell expansions like $VAR and $(cmd) 
 Fixed a bug where a hook writing to the terminal could corrupt an on-screen interactive prompt; hooks now run without terminal access 
 Fixed unbounded memory growth when an HTTP/SSE MCP server streams non-protocol data — response bodies now capped at 16 MB per SSE frame 
 Fixed Skill(name *) permission rules — the wildcard form now works as a prefix match, matching Bash(ls *) behavior 
 Fixed settings hot-reload not detecting edits to symlinked ~/.claude/settings.json 
 Fixed plugin details failing to load when the marketplace key differs from the manifest name 
 Fixed /model picker "Default" row not reflecting ANTHROPIC_DEFAULT_OPUS_MODEL / ANTHROPIC_DEFAULT_SONNET_MODEL overrides 
 Fixed spurious "stream idle timeout" 5 minutes after a response completed, caused by the watchdog timer not being cleared on stream cancellation 
 Fixed silent exit 1 when 10+ MCP servers are configured and the cache directory is unwritable — the error message now includes the underlying cause 
 Fixed a typing cursor blinking on tab names, list pointers, and select rows in dialogs 
 Fixed transcript view letter shortcuts not working after mouse click 
 Fixed Bash-mode up-arrow history repeating the first entry and clobbering the in-progress draft 
 Fixed pasting or dropping multiple images only inserting the last one 
 Fixed hyperlinks using unreadable dark navy on dark themes — they now adapt to the active theme 
 Fixed model picker showing a redundant "Current model" row for third-party users whose model is set to the opus alias 
 Fixed legacy Opus picker entry on PAYG 3P providers resolving to the same model as the default entry 
 Fixed mouse wheel scrolling speed in Cursor and VS Code 1.92–1.104; the trackpad now scrolls at a steady rate and the mouse wheel keeps ~3 lines per notch 
 Fixed scroll behavior in Windows Terminal and VS Code when attached to background sessions 
 Fixed MCP resources from disconnected servers lingering in @server: autocomplete 
 Fixed two-file diff snippets over-reporting the number of truncated lines by one 
 Fixed Grep results not relativizing Windows drive-letter paths and count mode reporting wrong totals for single-file paths 
 Fixed border-embedded text overflowing on CJK/emoji due to visual cell width miscalculation 
 Fixed fuzzy-match highlighting splitting emoji and astral-plane characters mid-pair 
 Fixed skill argument names containing regex metacharacters breaking argument substitution 
 Fixed ProgressBar rendering a full block for an almost-full fractional cell 
 Fixed task polling and fs.watch being resurrected when the last subscriber leaves while a fetch is in flight 
 Fixed plugin dependency resolution leaving a stale count when the manifest name differs from the source identifier 
 Fixed Insights Time-of-Day chart skewing when a session has an unparseable timestamp 
 Fixed keybindings using only the cmd/super/win modifier being flagged as unparseable 
 Fixed claude_code.active_time.total OpenTelemetry metric not being emitted in --print mode 
 Fixed claude plugin update not preserving cross-plugin symlinks inside a marketplace 
 [VSCode] Press Cmd/Ctrl+Shift+T to reopen the most recently closed session tab, configurable via claudeCode.enableReopenClosedSessionShortcut

</details>