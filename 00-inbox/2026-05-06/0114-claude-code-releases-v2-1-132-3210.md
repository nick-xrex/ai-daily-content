---
id: inbox_d4938234
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.132"
author: "ashwin-ant"
published_at: 2026-05-06T22:08:13+00:00
fetched_at: 2026-05-07T01:14:25.248756+00:00
content_hash: "32102ed51a7f3156b43036405631343333ffcca018f07810496f640148d6c502"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.132

<h2>What's changed</h2>
<ul>
<li>Added <code>CLAUDE_CODE_SESSION_ID</code> environment variable to the Bash tool subprocess environment, matching the <code>session_id</code> passed to hooks</li>
<li>Added <code>CLAUDE_CODE_DISABLE_ALTERNATE_SCREEN=1</code> env var to opt out of the fullscreen alternate-screen renderer and keep the conversation in the terminal's native scrollback</li>
<li>Added a "Pasting…" footer hint while a Ctrl+V image paste is being read from the clipboard</li>
<li>Fixed external SIGINT (e.g. IDE stop button, <code>kill -INT</code>) not running graceful shutdown — terminal modes are now restored and the <code>--resume</code> hint is printed instead of an abrupt exit</li>
<li>Fixed an uncaught exception when the terminal is closed or SSH disconnects mid-session under the native build</li>
<li>Fixed <code>--resume</code> failing with <code>no low surrogate in string</code> when a tool error truncation split an emoji; pre-corrupted sessions are sanitized on load</li>
<li>Fixed <code>--permission-mode</code> flag being ignored when resuming a plan-mode session with <code>-p --continue</code>/<code>--resume</code>, and plan mode not being re-applied after <code>ExitPlanMode</code> within the same session</li>
<li>Fixed fullscreen mode showing a blank screen after laptop sleep/wake or Ctrl+Z/<code>fg</code> until the next keystroke or stream output</li>
<li>Fixed cursor landing mid-grapheme on Ctrl+E/A/K/U/arrow keys when an Indic conjunct or ZWJ emoji wraps across lines</li>
<li>Fixed vim operators corrupting text containing decomposed (NFD) accented characters</li>
<li>Fixed pasting text starting with <code>/</code> silently swallowing the input or triggering an unknown-command reply</li>
<li>Fixed pasting dumping stray escape sequences into the prompt when focus events or mouse-tracking reports interleave with the bracketed paste</li>
<li>Fixed mouse wheel scrolling being too fast in Cursor and VS Code 1.92–1.104 due to an upstream xterm.js bug</li>
<li>Fixed scroll-wheel handling in JetBrains IDE 2025.2 terminals (spurious arrow keys, wrong-direction events, runaway acceleration)</li>
<li>Fixed <code>/usage</code> Ctrl+S hanging when copying the stats screenshot to the clipboard on Linux/X11</li>
<li>Fixed <code>/terminal-setup</code> showing a contradictory error in Windows Terminal — Shift+Enter is natively supported there</li>
<li>Fixed <code>/effort</code> picker not reflecting the <code>CLAUDE_CODE_EFFORT_LEVEL</code> env var override</li>
<li>Fixed <code>/status</code> showing the wrong default model for some users</li>
<li>Fixed slash command autocomplete popup being capped at ~3–5 visible commands instead of scaling with terminal height</li>
<li>Fixed statusline <code>context_window</code> token counts reflecting cumulative session totals instead of current context usage</li>
<li>Fixed Alt+T (thinking toggle) not working on macOS terminals without "Option as Meta" enabled (iTerm2, Terminal.app defaults)</li>
<li>Fixed dead keyboard input on Windows after re-opening a background session from <code>claude agents</code></li>
<li>Fixed unbounded memory growth (10GB+ RSS) when a stdio MCP server writes non-protocol data to stdout</li>
<li>Fixed MCP servers that connect but fail <code>tools/list</code> silently showing 0 tools — they now retry once and show "connected · tools fetch failed" in <code>/mcp</code></li>
<li>Fixed unauthorized claude.ai MCP connectors showing as "failed" instead of "needs auth", and headless <code>-p</code> mode retrying non-transient 4xx connection failures</li>
<li>Improved visual consistency in slash command dialogs and <code>/login</code>, <code>/upgrade</code>, <code>/extra-usage</code> dialog spacing</li>
<li>Updated the <code>/tui fullscreen</code> startup banner to describe additional renderer benefits (lower memory usage, mouse support, auto-copy on select)</li>
<li>Fixed Bedrock and Vertex 400 errors when <code>ENABLE_PROMPT_CACHING_1H</code> is set</li>
</ul>