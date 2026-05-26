---
id: inbox_83f9131a
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v12.7.3"
author: "thedotmack"
published_at: 2026-05-07T01:32:28+00:00
fetched_at: 2026-05-26T00:14:50.189889+00:00
content_hash: "b3faaff178468d48b88e17efef4861a95fef44d7f285d1a1dd6bad995a7b84bd"
lang: en
caption_quality: None
raw: true
topics: []
---

# v12.7.3

Patch release for the reliability fixes merged in PR #2344 . 
 
 Stops context-overflow and quota hard-stop failures from restarting observer generators and burning subscription quota. 
 Makes Stop hook transcript lookup failures non-blocking, so missing worktree transcript paths do not re-wake Claude Code in a loop. 
 Hardens MCP/plugin startup path resolution when host plugin-root environment variables are absent. 
 Accepts legacy install markers while keeping new marker writes on the JSON format. 
 Fixes export-memories to honor isolated data dirs, validate worker ports, and send the worker route's canonical session-id field. 
 Makes pending_messages repair safer and removes stale worker_pid assumptions from the current queue/schema path. 
 Adds a focused PR babysit status helper for low-noise review/check monitoring.