---
id: inbox_343f7328
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.140"
author: "ashwin-ant"
published_at: 2026-05-12T21:09:45+00:00
fetched_at: 2026-05-14T18:18:01.934573+00:00
content_hash: "3d766eb3afea9f70af27ca3322acecb652b56aa7643eedf9b719b0b4a6667006"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.140

What's changed 
 
 Improved Agent tool subagent_type matching to accept case- and separator-insensitive values (e.g. "Code Reviewer" resolves to code-reviewer ) 
 Updated agent color palette 
 Fixed /goal silently hanging when disableAllHooks or allowManagedHooksOnly is set — now shows a clear message instead of an indicator that never resolves 
 Fixed a regression in settings hot-reload where symlinked settings files caused misattributed change events and spurious ConfigChange hooks 
 Fixed claude --bg failing with "connection dropped mid-request" when the background service was about to idle-exit 
 Fixed background service startup failing on machines with enterprise endpoint security by allowing more time 
 Fixed remote managed settings not retrying on 401 — now retries once with a force-refreshed token 
 Fixed managed extraKnownMarketplaces auto-update policy not being persisted to known_marketplaces.json 
 Fixed /loop scheduling redundant wakeups to poll for background tasks that already notify on completion 
 Fixed a recurring event-loop stall on Windows when a missing executable (e.g. gh ) triggered synchronous where.exe re-spawns on every check 
 Fixed Read tool calls failing validation when offset is passed as a whitespace-padded or + -prefixed string 
 Fixed native terminal cursor not staying at the input caret when the terminal loses focus 
 Plugins now warn when a default component folder (e.g. commands/ ) is silently ignored because plugin.json sets the matching key. Shown in /doctor , claude plugin list , and /plugin .