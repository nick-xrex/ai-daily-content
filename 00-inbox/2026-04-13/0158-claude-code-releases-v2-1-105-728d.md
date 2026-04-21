---
id: inbox_59969104
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.105"
author: "ashwin-ant"
published_at: 2026-04-13T21:53:13+00:00
fetched_at: 2026-04-21T01:58:16.063297+00:00
content_hash: "728d810d486567bdfef1969272f73712bd0513225b7eef1b288e2d7352069395"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.105

<h2>What's changed</h2>
<ul>
<li>Added <code>path</code> parameter to the <code>EnterWorktree</code> tool to switch into an existing worktree of the current repository</li>
<li>Added PreCompact hook support: hooks can now block compaction by exiting with code 2 or returning <code>{"decision":"block"}</code></li>
<li>Added background monitor support for plugins via a top-level <code>monitors</code> manifest key that auto-arms at session start or on skill invoke</li>
<li><code>/proactive</code> is now an alias for <code>/loop</code></li>
<li>Improved stalled API stream handling: streams now abort after 5 minutes of no data and retry non-streaming instead of hanging indefinitely</li>
<li>Improved network error messages: connection errors now show a retry message immediately instead of a silent spinner</li>
<li>Improved file write display: long single-line writes (e.g. minified JSON) are now truncated in the UI instead of paginating across many screens</li>
<li>Improved <code>/doctor</code> layout with status icons; press <code>f</code> to have Claude fix reported issues</li>
<li>Improved <code>/config</code> labels and descriptions for clarity</li>
<li>Improved skill description handling: raised the listing cap from 250 to 1,536 characters and added a startup warning when descriptions are truncated</li>
<li>Improved <code>WebFetch</code> to strip <code>&lt;style&gt;</code> and <code>&lt;script&gt;</code> contents from fetched pages so CSS-heavy pages no longer exhaust the content budget before reaching actual text</li>
<li>Improved stale agent worktree cleanup to remove worktrees whose PR was squash-merged instead of keeping them indefinitely</li>
<li>Improved MCP large-output truncation prompt to give format-specific recipes (e.g. <code>jq</code> for JSON, computed Read chunk sizes for text)</li>
<li>Fixed images attached to queued messages (sent while Claude is working) being dropped</li>
<li>Fixed screen going blank when the prompt input wraps to a second line in long conversations</li>
<li>Fixed leading whitespace getting copied when selecting multi-line assistant responses in fullscreen mode</li>
<li>Fixed leading whitespace being trimmed from assistant messages, breaking ASCII art and indented diagrams</li>
<li>Fixed garbled bash output when commands print clickable file links (e.g. Python <code>rich</code>/<code>loguru</code> logging)</li>
<li>Fixed alt+enter not inserting a newline in terminals using ESC-prefix alt encoding, and Ctrl+J not inserting a newline (regression in 2.1.100)</li>
<li>Fixed duplicate "Creating worktree" text in EnterWorktree/ExitWorktree tool display</li>
<li>Fixed queued user prompts disappearing from focus mode</li>
<li>Fixed one-shot scheduled tasks re-firing repeatedly when the file watcher missed the post-fire cleanup</li>
<li>Fixed inbound channel notifications being silently dropped after the first message for Team/Enterprise users</li>
<li>Fixed marketplace plugins with <code>package.json</code> and lockfile not having dependencies installed automatically after install/update</li>
<li>Fixed marketplace auto-update leaving the official marketplace in a broken state when a plugin process holds files open during the update</li>
<li>Fixed "Resume this session with..." hint not printing on exit after <code>/resume</code>, <code>--worktree</code>, or <code>/branch</code></li>
<li>Fixed feedback survey shortcut keys firing when typed at the end of a longer prompt</li>
<li>Fixed stdio MCP server emitting malformed (non-JSON) output hanging the session instead of failing fast with "Connection closed"</li>
<li>Fixed MCP tools missing on the first turn of headless/remote-trigger sessions when MCP servers connect asynchronously</li>
<li>Fixed <code>/model</code> picker on AWS Bedrock in non-US regions persisting invalid <code>us.*</code> model IDs to <code>settings.json</code> when inference profile discovery is still in-flight</li>
<li>Fixed 429 rate-limit errors showing a raw JSON dump instead of a clean message for API-key, Bedrock, and Vertex users</li>
<li>Fixed crash on resume when session contains malformed text blocks</li>
<li>Fixed <code>/help</code> dropping the tab bar, Shortcuts heading, and footer at short terminal heights</li>
<li>Fixed malformed keybinding entry values in <code>keybindings.json</code> being silently loaded instead of rejected with a clear error</li>
<li>Fixed <code>CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC</code> in one project's settings permanently disabling usage metrics for all projects on the machine</li>
<li>Fixed washed-out 16-color palette when using Ghostty, Kitty, Alacritty, WezTerm, foot, rio, or Contour over SSH/mosh</li>
<li>Fixed Bash tool suggesting <code>acceptEdits</code> permission mode when exiting plan mode would downgrade from a higher permission level</li>
</ul>