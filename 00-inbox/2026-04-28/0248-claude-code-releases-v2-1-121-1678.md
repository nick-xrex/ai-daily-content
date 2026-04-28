---
id: inbox_cb7cb00d
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.121"
author: "ashwin-ant"
published_at: 2026-04-28T00:31:31+00:00
fetched_at: 2026-04-28T02:48:06.876716+00:00
content_hash: "16788d1273fc5bb86a4b9303c2637518ee66fb0d8e140e20efd10be54aa1f587"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.121

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