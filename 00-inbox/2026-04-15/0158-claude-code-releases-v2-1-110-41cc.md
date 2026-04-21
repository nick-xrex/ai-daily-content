---
id: inbox_5357f42a
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.110"
author: "ashwin-ant"
published_at: 2026-04-15T23:21:43+00:00
fetched_at: 2026-04-21T01:58:16.054227+00:00
content_hash: "41ccb028442b47db456b92d6f742264b4f59fb912ed25abb632a0c80dc87e20f"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.110

<h2>What's changed</h2>
<ul>
<li>Added <code>/tui</code> command and <code>tui</code> setting — run <code>/tui fullscreen</code> to switch to flicker-free rendering in the same conversation</li>
<li>Changed <code>Ctrl+O</code> to toggle between normal and verbose transcript only; focus view is now toggled separately with the new <code>/focus</code> command</li>
<li>Added push notification tool — Claude can send mobile push notifications when Remote Control and "Push when Claude decides" config are enabled</li>
<li>Added <code>autoScrollEnabled</code> config to disable conversation auto-scroll in fullscreen mode</li>
<li>Added option to show Claude's last response as commented context in the <code>Ctrl+G</code> external editor (enable via <code>/config</code>)</li>
<li>Improved <code>/plugin</code> Installed tab — items needing attention and favorites appear at the top, disabled items are hidden behind a fold, and <code>f</code> favorites the selected item</li>
<li>Improved <code>/doctor</code> to warn when an MCP server is defined in multiple config scopes with different endpoints</li>
<li><code>--resume</code>/<code>--continue</code> now resurrects unexpired scheduled tasks</li>
<li><code>/autocompact</code>, <code>/context</code>, <code>/exit</code>, and <code>/reload-plugins</code> now work from Remote Control (mobile/web) clients</li>
<li>Write tool now informs the model when you edit the proposed content in the IDE diff before accepting</li>
<li>Bash tool now enforces the documented maximum timeout instead of accepting arbitrarily large values</li>
<li>SDK/headless sessions now read <code>TRACEPARENT</code>/<code>TRACESTATE</code> from the environment for distributed trace linking</li>
<li>Session recap is now enabled for users with telemetry disabled (Bedrock, Vertex, Foundry, <code>DISABLE_TELEMETRY</code>). Opt out via <code>/config</code> or <code>CLAUDE_CODE_ENABLE_AWAY_SUMMARY=0</code>.</li>
<li>Fixed MCP tool calls hanging indefinitely when the server connection drops mid-response on SSE/HTTP transports</li>
<li>Fixed non-streaming fallback retries causing multi-minute hangs when the API is unreachable</li>
<li>Fixed session recap, local slash-command output, and other system status lines not appearing in focus mode</li>
<li>Fixed high CPU usage in fullscreen when text is selected while a tool is running</li>
<li>Fixed plugin install not honoring dependencies declared in <code>plugin.json</code> when the marketplace entry omits them; <code>/plugin</code> install now lists auto-installed dependencies</li>
<li>Fixed skills with <code>disable-model-invocation: true</code> failing when invoked via <code>/&lt;skill&gt;</code> mid-message</li>
<li>Fixed <code>--resume</code> sometimes showing the first prompt instead of the <code>/rename</code> name for sessions still running or exited uncleanly</li>
<li>Fixed queued messages briefly appearing twice during multi-tool-call turns</li>
<li>Fixed session cleanup not removing the full session directory including subagent transcripts</li>
<li>Fixed dropped keystrokes after the CLI relaunches (e.g. <code>/tui</code>, provider setup wizards)</li>
<li>Fixed garbled startup rendering in macOS Terminal.app and other terminals that don't support synchronized output</li>
<li>Hardened "Open in editor" actions against command injection from untrusted filenames</li>
<li>Fixed <code>PermissionRequest</code> hooks returning <code>updatedInput</code> not being re-checked against <code>permissions.deny</code> rules; <code>setMode:'bypassPermissions'</code> updates now respect <code>disableBypassPermissionsMode</code></li>
<li>Fixed <code>PreToolUse</code> hook <code>additionalContext</code> being dropped when the tool call fails</li>
<li>Fixed stdio MCP servers that print stray non-JSON lines to stdout being disconnected on the first stray line (regression in 2.1.105)</li>
<li>Fixed headless/SDK session auto-title firing an extra Haiku request when <code>CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC</code> or <code>CLAUDE_CODE_DISABLE_TERMINAL_TITLE</code> is set</li>
<li>Fixed potential excessive memory allocation when piped (non-TTY) Ink output contains a single very wide line</li>
<li>Fixed <code>/skills</code> menu not scrolling when the list overflows the modal in fullscreen mode</li>
<li>Fixed Remote Control sessions showing a generic error instead of prompting for re-login when the session is too old</li>
<li>Fixed Remote Control session renames from claude.ai not persisting the title to the local CLI session</li>
</ul>