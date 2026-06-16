---
id: inbox_83f9131a
date: 2026-05-07
source_ref: "[[00-inbox/.../inbox_83f9131a]]"
title: "v12.7.3"
url: https://github.com/thedotmack/claude-mem/releases/tag/v12.7.3
source: claude-mem-releases
published_at: 2026-05-07T01:32:28+00:00
fetched_at: 2026-06-16T00:46:03.124500+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: ""
key_points:
tags: []
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## v12.7.3



### 重點

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v12.7.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v12.7.3

Patch release for the reliability fixes merged in PR #2344 . 
 
 Stops context-overflow and quota hard-stop failures from restarting observer generators and burning subscription quota. 
 Makes Stop hook transcript lookup failures non-blocking, so missing worktree transcript paths do not re-wake Claude Code in a loop. 
 Hardens MCP/plugin startup path resolution when host plugin-root environment variables are absent. 
 Accepts legacy install markers while keeping new marker writes on the JSON format. 
 Fixes export-memories to honor isolated data dirs, validate worker ports, and send the worker route's canonical session-id field. 
 Makes pending_messages repair safer and removes stale worker_pid assumptions from the current queue/schema path. 
 Adds a focused PR babysit status helper for low-noise review/check monitoring.

</details>