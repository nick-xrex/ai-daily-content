---
id: inbox_f5c76558
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.118"
author: "ashwin-ant"
published_at: 2026-04-23T00:42:21+00:00
fetched_at: 2026-04-24T02:46:11.202106+00:00
content_hash: "bcceb76da423f3d7acd36ba2e3cd480a76c9f81d4f3c57b49ed69008d47856f4"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.118

<h2>What's changed</h2>
<ul>
<li>Added vim visual mode (<code>v</code>) and visual-line mode (<code>V</code>) with selection, operators, and visual feedback</li>
<li>Merged <code>/cost</code> and <code>/stats</code> into <code>/usage</code> — both remain as typing shortcuts that open the relevant tab</li>
<li>Create and switch between named custom themes from <code>/theme</code>, or hand-edit JSON files in <code>~/.claude/themes/</code>; plugins can also ship themes via a <code>themes/</code> directory</li>
<li>Hooks can now invoke MCP tools directly via <code>type: "mcp_tool"</code></li>
<li>Added <code>DISABLE_UPDATES</code> env var to completely block all update paths including manual <code>claude update</code> — stricter than <code>DISABLE_AUTOUPDATER</code></li>
<li>WSL on Windows can now inherit Windows-side managed settings via the <code>wslInheritsWindowsSettings</code> policy key</li>
<li>Auto mode: include <code>"$defaults"</code> in <code>autoMode.allow</code>, <code>autoMode.soft_deny</code>, or <code>autoMode.environment</code> to add custom rules alongside the built-in list instead of replacing it</li>
<li>Added a "Don't ask again" option to the auto mode opt-in prompt</li>
<li>Added <code>claude plugin tag</code> to create release git tags for plugins with version validation</li>
<li><code>--continue</code>/<code>--resume</code> now find sessions that added the current directory via <code>/add-dir</code></li>
<li><code>/color</code> now syncs the session accent color to claude.ai/code when Remote Control is connected</li>
<li>The <code>/model</code> picker now honors <code>ANTHROPIC_DEFAULT_*_MODEL_NAME</code>/<code>_DESCRIPTION</code> overrides when using a custom <code>ANTHROPIC_BASE_URL</code> gateway</li>
<li>When auto-update skips a plugin due to another plugin's version constraint, the skip now appears in <code>/doctor</code> and the <code>/plugin</code> Errors tab</li>
<li>Fixed <code>/mcp</code> menu hiding OAuth Authenticate/Re-authenticate actions for servers configured with <code>headersHelper</code>, and HTTP/SSE MCP servers with custom headers being stuck in "needs authentication" after a transient 401</li>
<li>Fixed MCP servers whose OAuth token response omits <code>expires_in</code> requiring re-authentication every hour</li>
<li>Fixed MCP step-up authorization silently refreshing instead of prompting for re-consent when the server's <code>insufficient_scope</code> 403 names a scope the current token already has</li>
<li>Fixed an unhandled promise rejection when an MCP server's OAuth flow times out or is cancelled</li>
<li>Fixed MCP OAuth refresh proceeding without its cross-process lock under contention</li>
<li>Fixed macOS keychain race where a concurrent MCP token refresh could overwrite a freshly-refreshed OAuth token, causing unexpected "Please run /login" prompts</li>
<li>Fixed OAuth token refresh failing when the server revokes a token before its local expiry time</li>
<li>Fixed credential save crash on Linux/Windows corrupting <code>~/.claude/.credentials.json</code></li>
<li>Fixed <code>/login</code> having no effect in a session launched with <code>CLAUDE_CODE_OAUTH_TOKEN</code> — the env token is now cleared so disk credentials take effect</li>
<li>Fixed unreadable text in the "new messages" scroll pill and <code>/plugin</code> badges</li>
<li>Fixed plan acceptance dialog offering "auto mode" instead of "bypass permissions" when running with <code>--dangerously-skip-permissions</code></li>
<li>Fixed agent-type hooks failing with "Messages are required for agent hooks" when configured for events other than <code>Stop</code> or <code>SubagentStop</code></li>
<li>Fixed <code>prompt</code> hooks re-firing on tool calls made by an agent-hook verifier subagent</li>
<li>Fixed <code>/fork</code> writing the full parent conversation to disk per fork — now writes a pointer and hydrates on read</li>
<li>Fixed Alt+K / Alt+X / Alt+^ / Alt+_ freezing keyboard input</li>
<li>Fixed connecting to a remote session overwriting your local <code>model</code> setting in <code>~/.claude/settings.json</code></li>
<li>Fixed typeahead showing "No commands match" error when pasting file paths that start with <code>/</code></li>
<li>Fixed <code>plugin install</code> on an already-installed plugin not re-resolving a dependency installed at the wrong version</li>
<li>Fixed unhandled errors from file watcher on invalid paths or fd exhaustion</li>
<li>Fixed Remote Control sessions getting archived on transient CCR initialization blips during JWT refresh</li>
<li>Fixed subagents resumed via <code>SendMessage</code> not restoring the explicit <code>cwd</code> they were spawned with</li>
</ul>