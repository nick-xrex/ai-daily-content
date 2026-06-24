---
id: inbox_fac29129
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.191"
author: "ashwin-ant"
published_at: 2026-06-24T21:58:12+00:00
fetched_at: 2026-06-24T22:00:15.940056+00:00
content_hash: "48c2fd3e1377753b482a839581e8108b3bc2080e8f21adfe2484d42fc2c80148"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.191

What's changed 
 
 Added /rewind support for resuming a conversation from before /clear was run 
 Fixed scroll position jumping to the bottom while reading earlier output during a streaming response 
 Fixed background agents resurrecting after being stopped — stopping an agent from the tasks panel is now permanent 
 Fixed /voice showing a generic "not available" message when disabled by an organization's policy — it now explains the restriction 
 Fixed /login URL opening truncated in Windows Terminal when it wraps across lines 
 Fixed Cmd+click on links in fullscreen mode for Ghostty over ssh/tmux 
 Fixed claude agents sending builtin slash commands like /usage to background sessions as prompt text instead of showing a hint 
 Fixed claude agents job rows showing full filesystem paths for pasted images instead of the [Image #N] placeholder 
 Fixed hooks with comma-separated matchers (e.g. "Bash,PowerShell" ) silently never firing 
 Fixed /permissions Recently-denied tab: approving a denial now persists on close instead of being silently discarded 
 Fixed the agent panel jumping by one row when scrolling the roster past the overflow cap 
 Fixed the welcome splash art overflowing the default 80×24 macOS Terminal window 
 Fixed managed settings: forceRemoteSettingsRefresh now takes effect when set via MDM or file policy, and the fetch sends Cache-Control: no-cache to prevent proxies from serving stale responses 
 Improved sandbox network permission dialog: hosts you allow with "Yes" are now remembered for the rest of the session instead of re-prompting on every connection 
 Improved MCP server reliability: capability discovery ( tools/list , prompts/list , resources/list ) now retries transient network errors with short backoff 
 Improved MCP OAuth: discovery and token requests now retry once after transient network errors, and headless environments skip the browser popup and go straight to the paste-the-URL prompt 
 Improved MCP error messages: HTTP 404 errors now show the URL and point to your MCP config 
 Improved vim mode prompt-history search (NORMAL / ) to hint how to reach slash commands 
 Reduced CPU usage during streaming responses by ~37% by coalescing text updates to 100ms 
 Reduced long-session memory growth from terminal output cache