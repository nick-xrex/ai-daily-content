---
id: inbox_bf677b5e
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.119"
author: "ashwin-ant"
published_at: 2026-04-23T23:24:19+00:00
fetched_at: 2026-04-24T02:46:11.140176+00:00
content_hash: "e65a6e629f1ebef472fbf71e59c569cd5a46a901cab37dfdbb3abedfc808e924"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.119

<h2>What's changed</h2>
<ul>
<li><code>/config</code> settings (theme, editor mode, verbose, etc.) now persist to <code>~/.claude/settings.json</code> and participate in project/local/policy override precedence</li>
<li>Added <code>prUrlTemplate</code> setting to point the footer PR badge at a custom code-review URL instead of github.com</li>
<li>Added <code>CLAUDE_CODE_HIDE_CWD</code> environment variable to hide the working directory in the startup logo</li>
<li><code>--from-pr</code> now accepts GitLab merge-request, Bitbucket pull-request, and GitHub Enterprise PR URLs</li>
<li><code>--print</code> mode now honors the agent's <code>tools:</code> and <code>disallowedTools:</code> frontmatter, matching interactive-mode behavior</li>
<li><code>--agent &lt;name&gt;</code> now honors the agent definition's <code>permissionMode</code> for built-in agents</li>
<li>PowerShell tool commands can now be auto-approved in permission mode, matching Bash behavior</li>
<li>Hooks: <code>PostToolUse</code> and <code>PostToolUseFailure</code> hook inputs now include <code>duration_ms</code> (tool execution time, excluding permission prompts and PreToolUse hooks)</li>
<li>Subagent and SDK MCP server reconfiguration now connects servers in parallel instead of serially</li>
<li>Plugins pinned by another plugin's version constraint now auto-update to the highest satisfying git tag</li>
<li>Vim mode: Esc in INSERT no longer pulls a queued message back into the input; press Esc again to interrupt</li>
<li>Slash command suggestions now highlight the characters that matched your query</li>
<li>Slash command picker now wraps long descriptions onto a second line instead of truncating</li>
<li><code>owner/repo#N</code> shorthand links in output now use your git remote's host instead of always pointing at github.com</li>
<li>Security: <code>blockedMarketplaces</code> now correctly enforces <code>hostPattern</code> and <code>pathPattern</code> entries</li>
<li>OpenTelemetry: <code>tool_result</code> and <code>tool_decision</code> events now include <code>tool_use_id</code>; <code>tool_result</code> also includes <code>tool_input_size_bytes</code></li>
<li>Status line: stdin JSON now includes <code>effort.level</code> and <code>thinking.enabled</code></li>
<li>Fixed pasting CRLF content (Windows clipboards, Xcode console) inserting an extra blank line between every line</li>
<li>Fixed multi-line paste losing newlines in terminals using kitty keyboard protocol sequences inside bracketed paste</li>
<li>Fixed Glob and Grep tools disappearing on native macOS/Linux builds when the Bash tool is denied via permissions</li>
<li>Fixed scrolling up in fullscreen mode snapping back to the bottom every time a tool finishes</li>
<li>Fixed MCP HTTP connections failing with "Invalid OAuth error response" when servers returned non-JSON bodies for OAuth discovery requests</li>
<li>Fixed Rewind overlay showing "(no prompt)" for messages with image attachments</li>
<li>Fixed auto mode overriding plan mode with conflicting "Execute immediately" instructions</li>
<li>Fixed async <code>PostToolUse</code> hooks that emit no response payload writing empty entries to the session transcript</li>
<li>Fixed spinner staying on when a subagent task notification is orphaned in the queue</li>
<li>Tool search is now disabled by default on Vertex AI to avoid an unsupported beta header error (opt in with <code>ENABLE_TOOL_SEARCH</code>)</li>
<li>Fixed <code>@</code>-file Tab completion replacing the entire prompt when used inside a slash command with an absolute path</li>
<li>Fixed a stray <code>p</code> character appearing at the prompt on startup in macOS Terminal.app via Docker or SSH</li>
<li>Fixed <code>${ENV_VAR}</code> placeholders in <code>headers</code> for HTTP/SSE/WebSocket MCP servers not being substituted before requests</li>
<li>Fixed MCP OAuth client secret stored via <code>--client-secret</code> not being sent during token exchange for servers requiring <code>client_secret_post</code></li>
<li>Fixed <code>/skills</code> Enter key closing the dialog instead of pre-filling <code>/&lt;skill-name&gt;</code> in the prompt</li>
<li>Fixed <code>/agents</code> detail view mislabeling built-in tools unavailable to subagents as "Unrecognized"</li>
<li>Fixed MCP servers from plugins not spawning on Windows when the plugin cache was incomplete</li>
<li>Fixed <code>/export</code> showing the current default model instead of the model the conversation actually used</li>
<li>Fixed verbose output setting not persisting after restart</li>
<li>Fixed <code>/usage</code> progress bars overlapping with their "Resets …" labels</li>
<li>Fixed plugin MCP servers failing when <code>${user_config.*}</code> references an optional field left blank</li>
<li>Fixed list items containing a sentence-final number wrapping the number onto its own line</li>
<li>Fixed <code>/plan</code> and <code>/plan open</code> not acting on the existing plan when entering plan mode</li>
<li>Fixed skills invoked before auto-compaction being re-executed against the next user message</li>
<li>Fixed <code>/reload-plugins</code> and <code>/doctor</code> reporting load errors for disabled plugins</li>
<li>Fixed Agent tool with <code>isolation: "worktree"</code> reusing stale worktrees from prior sessions</li>
<li>Fixed disabled MCP servers appearing as "failed" in <code>/status</code></li>
<li>Fixed <code>TaskList</code> returning tasks in arbitrary filesystem order instead of sorted by ID</li>
<li>Fixed spurious "GitHub API rate limit exceeded" hints when <code>gh</code> output contained PR titles mentioning "rate limit"</li>
<li>Fixed SDK/bridge <code>read_file</code> not correctly enforcing size cap on growing files</li>
<li>Fixed PR not linked to session when working in a git worktree</li>
<li>Fixed <code>/doctor</code> warning about MCP server entries overridden by a higher-precedence scope</li>
<li>Windows: removed false-positive "Windows requires 'cmd /c' wrapper" MCP config warning</li>
<li>[VSCode] Fixed voice dictation's first recording producing nothing on macOS while the microphone permission prompt is showing</li>
</ul>