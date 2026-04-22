---
id: inbox_113aa3f4
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.117"
author: "ashwin-ant"
published_at: 2026-04-22T00:04:40+00:00
fetched_at: 2026-04-22T01:54:33.273131+00:00
content_hash: "717c1519168a80cef56d0d6e1642b7122a2bb537a8be2b0e641cba7a32a723da"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.117

<h2>What's changed</h2>
<ul>
<li>Forked subagents can now be enabled on external builds by setting <code>CLAUDE_CODE_FORK_SUBAGENT=1</code></li>
<li>Agent frontmatter <code>mcpServers</code> are now loaded for main-thread agent sessions via <code>--agent</code></li>
<li>Improved <code>/model</code>: selections now persist across restarts even when the project pins a different model, and the startup header shows when the active model comes from a project or managed-settings pin</li>
<li>The <code>/resume</code> command now offers to summarize stale, large sessions before re-reading them, matching the existing <code>--resume</code> behavior</li>
<li>Faster startup when both local and claude.ai MCP servers are configured (concurrent connect now default)</li>
<li><code>plugin install</code> on an already-installed plugin now installs any missing dependencies instead of stopping at "already installed"</li>
<li>Plugin dependency errors now say "not installed" with an install hint, and <code>claude plugin marketplace add</code> now auto-resolves missing dependencies from configured marketplaces</li>
<li>Managed-settings <code>blockedMarketplaces</code> and <code>strictKnownMarketplaces</code> are now enforced on plugin install, update, refresh, and autoupdate</li>
<li>Advisor Tool (experimental): dialog now carries an "experimental" label, learn-more link, and startup notification when enabled; sessions no longer get stuck with "Advisor tool result content could not be processed" errors on every prompt and <code>/compact</code></li>
<li>The <code>cleanupPeriodDays</code> retention sweep now also covers <code>~/.claude/tasks/</code>, <code>~/.claude/shell-snapshots/</code>, and <code>~/.claude/backups/</code></li>
<li>OpenTelemetry: <code>user_prompt</code> events now include <code>command_name</code> and <code>command_source</code> for slash commands; <code>cost.usage</code>, <code>token.usage</code>, <code>api_request</code>, and <code>api_error</code> now include an <code>effort</code> attribute when the model supports effort levels. Custom/MCP command names are redacted unless <code>OTEL_LOG_TOOL_DETAILS=1</code> is set</li>
<li>Native builds on macOS and Linux: the <code>Glob</code> and <code>Grep</code> tools are replaced by embedded <code>bfs</code> and <code>ugrep</code> available through the Bash tool — faster searches without a separate tool round-trip (Windows and npm-installed builds unchanged)</li>
<li>Windows: cached <code>where.exe</code> executable lookups per process for faster subprocess launches</li>
<li>Default effort for Pro/Max subscribers on Opus 4.6 and Sonnet 4.6 is now <code>high</code> (was <code>medium</code>)</li>
<li>Fixed Plain-CLI OAuth sessions dying with "Please run /login" when the access token expires mid-session — the token is now refreshed reactively on 401</li>
<li>Fixed <code>WebFetch</code> hanging on very large HTML pages by truncating input before HTML-to-markdown conversion</li>
<li>Fixed a crash when a proxy returns HTTP 204 No Content — now surfaces a clear error instead of a <code>TypeError</code></li>
<li>Fixed <code>/login</code> having no effect when launched with <code>CLAUDE_CODE_OAUTH_TOKEN</code> env var and that token expires</li>
<li>Fixed prompt-input undo (<code>Ctrl+_</code>) doing nothing immediately after typing, and skipping a state on each undo step</li>
<li>Fixed <code>NO_PROXY</code> not being respected for remote API requests when running under Bun</li>
<li>Fixed rare spurious escape/return triggers when key names arrive as coalesced text over slow connections</li>
<li>Fixed SDK <code>reload_plugins</code> reconnecting all user MCP servers serially</li>
<li>Fixed Bedrock application-inference-profile requests failing with 400 when backed by Opus 4.7 with thinking disabled</li>
<li>Fixed MCP <code>elicitation/create</code> requests auto-cancelling in print/SDK mode when the server finishes connecting mid-turn</li>
<li>Fixed subagents running a different model than the main agent incorrectly flagging file reads with a malware warning</li>
<li>Fixed idle re-render loop when background tasks are present, reducing memory growth on Linux</li>
<li>[VSCode] Fixed "Manage Plugins" panel breaking when multiple large marketplaces are configured</li>
<li>Fixed Opus 4.7 sessions showing inflated <code>/context</code> percentages and autocompacting too early — Claude Code was computing against a 200K context window instead of Opus 4.7's native 1M</li>
</ul>