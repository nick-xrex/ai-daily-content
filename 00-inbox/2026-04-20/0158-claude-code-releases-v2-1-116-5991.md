---
id: inbox_7349264c
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.116"
author: "ashwin-ant"
published_at: 2026-04-20T22:18:28+00:00
fetched_at: 2026-04-21T01:58:16.035485+00:00
content_hash: "599181142082ec0e8d9438823f01651d426e5c21bd3057f2d7c1af950a86241f"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.116

<h2>What's changed</h2>
<ul>
<li><code>/resume</code> on large sessions is significantly faster (up to 67% on 40MB+ sessions) and handles sessions with many dead-fork entries more efficiently</li>
<li>Faster MCP startup when multiple stdio servers are configured; <code>resources/templates/list</code> is now deferred to first <code>@</code>-mention</li>
<li>Smoother fullscreen scrolling in VS Code, Cursor, and Windsurf terminals — <code>/terminal-setup</code> now configures the editor's scroll sensitivity</li>
<li>Thinking spinner now shows progress inline ("still thinking", "thinking more", "almost done thinking"), replacing the separate hint row</li>
<li><code>/config</code> search now matches option values (e.g. searching "vim" finds the Editor mode setting)</li>
<li><code>/doctor</code> can now be opened while Claude is responding, without waiting for the current turn to finish</li>
<li><code>/reload-plugins</code> and background plugin auto-update now auto-install missing plugin dependencies from marketplaces you've already added</li>
<li>Bash tool now surfaces a hint when <code>gh</code> commands hit GitHub's API rate limit, so agents can back off instead of retrying</li>
<li>The Usage tab in Settings now shows your 5-hour and weekly usage immediately and no longer fails when the usage endpoint is rate-limited</li>
<li>Agent frontmatter <code>hooks:</code> now fire when running as a main-thread agent via <code>--agent</code></li>
<li>Slash command menu now shows "No commands match" when your filter has zero results, instead of disappearing</li>
<li>Security: sandbox auto-allow no longer bypasses the dangerous-path safety check for <code>rm</code>/<code>rmdir</code> targeting <code>/</code>, <code>$HOME</code>, or other critical system directories</li>
<li>Fixed Devanagari and other Indic scripts rendering with broken column alignment in the terminal UI</li>
<li>Fixed Ctrl+- not triggering undo in terminals using the Kitty keyboard protocol (iTerm2, Ghostty, kitty, WezTerm, Windows Terminal)</li>
<li>Fixed Cmd+Left/Right not jumping to line start/end in terminals that use the Kitty keyboard protocol (Warp fullscreen, kitty, Ghostty, WezTerm)</li>
<li>Fixed Ctrl+Z hanging the terminal when Claude Code is launched via a wrapper process (e.g. <code>npx</code>, <code>bun run</code>)</li>
<li>Fixed scrollback duplication in inline mode where resizing the terminal or large output bursts would repeat earlier conversation history</li>
<li>Fixed modal search dialogs overflowing the screen at short terminal heights, hiding the search box and keyboard hints</li>
<li>Fixed scattered blank cells and disappearing composer chrome in the VS Code integrated terminal during scrolling</li>
<li>Fixed an intermittent API 400 error related to cache control TTL ordering that could occur when a parallel request completed during request setup</li>
<li>Fixed <code>/branch</code> rejecting conversations with transcripts larger than 50MB</li>
<li>Fixed <code>/resume</code> silently showing an empty conversation on large session files instead of reporting the load error</li>
<li>Fixed <code>/plugin</code> Installed tab showing the same item twice when it appears under Needs attention or Favorites</li>
<li>Fixed <code>/update</code> and <code>/tui</code> not working after entering a worktree mid-session</li>
</ul>