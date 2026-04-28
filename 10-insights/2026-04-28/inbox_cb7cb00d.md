---
id: inbox_cb7cb00d
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0248-claude-code-releases-v2-1-121-1678]]"
title: "v2.1.121"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.121
source: claude-code-releases
published_at: 2026-04-28T00:31:31+00:00
fetched_at: 2026-04-28T02:52:44.800232+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.121 發布，包含超過 30 項功能更新與錯誤修復。修復了嚴重的記憶體洩漏問題：處理多張圖片會導致 RSS 成長至數 GB，`/usage` 命令會洩漏約 2GB 記憶體。新增 MCP 伺服器配置 `alwaysLoad` 選項以跳過工具搜尋延遲，PostToolUse 掛鉤現在支援全工具輸出替換。UI 方面改進包括全螢幕模式下滾動行為修正、可捲動對話框、在 iTerm2 上啟用剪貼簿訪問。這些修復對長期執行複雜工作流程的開發者尤為重要，特別是在處理大型專案時提升穩定性。"
key_points:
  - "修復 2GB+ 級別記憶體洩漏：圖片處理引發 RSS 異常成長，`/usage` 命令洩漏約 2GB"
  - "MCP 伺服器新增 `alwaysLoad` 選項，所有掛鉤支援全工具輸出替換"
  - "UI 改進：全螢幕滾動修正、可捲動對話框、iTerm2 剪貼簿支援"
tags: [claude-code, memory-leak-fix, mcp-improvements, ui-enhancements, stability]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.121

Claude Code v2.1.121 發布，包含超過 30 項功能更新與錯誤修復。修復了嚴重的記憶體洩漏問題：處理多張圖片會導致 RSS 成長至數 GB，`/usage` 命令會洩漏約 2GB 記憶體。新增 MCP 伺服器配置 `alwaysLoad` 選項以跳過工具搜尋延遲，PostToolUse 掛鉤現在支援全工具輸出替換。UI 方面改進包括全螢幕模式下滾動行為修正、可捲動對話框、在 iTerm2 上啟用剪貼簿訪問。這些修復對長期執行複雜工作流程的開發者尤為重要，特別是在處理大型專案時提升穩定性。

### 重點
- 修復 2GB+ 級別記憶體洩漏：圖片處理引發 RSS 異常成長，`/usage` 命令洩漏約 2GB
- MCP 伺服器新增 `alwaysLoad` 選項，所有掛鉤支援全工具輸出替換
- UI 改進：全螢幕滾動修正、可捲動對話框、iTerm2 剪貼簿支援

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.121)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<h2>What's changed</h2>
<ul>
<li>Added <code>alwaysLoad</code> option to MCP server config — when <code>true</code>, all tools from that server skip tool-search deferral and are always available</li>
<li>Added <code>claude plugin prune</code> to remove orphaned auto-installed plugin dependencies; <code>plugin uninstall --prune</code> cascades</li>
<li>Added a type-to-filter search box to <code>/skills</code> so you can find a skill in long lists without scrolling</li>
<li>PostToolUse hooks can now replace tool output for all tools via <code>hookSpecificOutput.updatedToolOutput</code> (previously MCP-only)</li>
<li>Fullscreen mode: typing into the prompt no longer jumps scroll back to the bottom after you've scrolled up to read earlier output</li>
<li>Dialogs that overflow the terminal are now scrollable with arrow keys, PgUp/PgDn, home/end, and mouse wheel in both fullscreen and non-fullscreen modes</li>
<li>Clicking any line of a long URL that wraps across rows in fullscreen mode now opens the full URL</li>
<li>SDK and <code>claude -p</code>: <code>CLAUDE_CODE_FORK_SUBAGENT=1</code> now works in non-interactive sessions</li>
<li><code>--dangerously-skip-permissions</code> no longer prompts for writes to <code>.claude/skills/</code>, <code>.claude/agents/</code>, and <code>.claude/commands/</code></li>
<li><code>/terminal-setup</code> now enables iTerm2's "Applications in terminal may access clipboard" setting so <code>/copy</code> works, including from tmux</li>
<li>MCP servers that hit a transient error during startup now auto-retry up to 3 times instead of staying disconnected</li>
<li>The terminal tab session title is now generated in your configured <code>language</code> setting</li>
<li>Claude.ai connectors with the same upstream URL are now deduplicated instead of appearing as duplicates</li>
<li>Vertex AI: support X.509 certificate-based Workload Identity Federation (mTLS ADC)</li>
<li>Faster startup after upgrading: removed the Recent Activity panel from the release-notes splash</li>
<li>LSP diagnostic summaries now expand on click/ctrl+o and show the expand hint</li>
<li>SDK: <code>mcp_authenticate</code> now supports <code>redirectUri</code> for custom scheme completion and claude.ai connectors</li>
<li>OpenTelemetry: added <code>stop_reason</code>, <code>gen_ai.response.finish_reasons</code>, and <code>user_system_prompt</code> (gated behind <code>OTEL_LOG_USER_PROMPTS</code>) to LLM request spans</li>
<li>[VSCode] Voice dictation now respects the <code>accessibility.voice.speechLanguage</code> setting when no Claude Code language is configured</li>
<li>[VSCode] <code>/context</code> now opens a native token usage dialog</li>
<li>Fixed unbounded memory growth (multi-GB RSS) when processing many images in a session</li>
<li>Fixed <code>/usage</code> leaking up to ~2GB of memory on machines with large transcript histories</li>
<li>Fixed memory leak when long-running tools fail to emit a clear progress event</li>
<li>Fixed Bash tool becoming permanently unusable when the directory Claude was started in is deleted or moved mid-session</li>
<li>Fixed <code>--resume</code> crashing on startup in external builds</li>
<li>Fixed <code>--resume</code> failing on large sessions when a transcript line was corrupted by an unclean shutdown — the corrupt line is now skipped</li>
<li>Fixed <code>thinking.type.enabled is not supported</code> error when using Bedrock application inference profile ARNs</li>
<li>Fixed Microsoft 365 MCP OAuth failing with duplicate or unsupported <code>prompt</code> parameter</li>
<li>Fixed scrollback duplication when pressing Ctrl+L or triggering a redraw in non-fullscreen mode on tmux, GNOME Terminal, Windows Terminal, and Konsole</li>
<li>Fixed claude.ai MCP connectors silently disappearing when the connector-list fetch hits a transient auth error at startup</li>
<li>Fixed "Always allow" rules for built-in tools in remote sessions not surviving worker restarts</li>
<li>Fixed <code>NO_PROXY</code> not being respected for all HTTP clients when set via <code>managed-settings.json</code> under the native build</li>
<li>Fixed managed settings approval prompt exiting the session even when accepted — now applies settings and continues</li>
<li>Fixed <code>/usage</code> returning "rate limited" after a stale OAuth token — now refreshes automatically</li>
<li>Fixed invalid legacy enum values in <code>settings.json</code> invalidating the entire settings file</li>
<li>Fixed <code>/usage</code> dialog content being clipped when no-flicker mode is off</li>
<li>Fixed <code>/focus</code> showing "Unknown command" when the fullscreen renderer is off — now explains how to enable it</li>
<li>Fixed embedded grep/find/rg shell wrappers failing when the running binary is deleted mid-session — now falls back to installed tools</li>
<li>Reduced peak file descriptor usage during <code>find</code> in the Bash tool on large directory trees</li>
</ul>

</details>