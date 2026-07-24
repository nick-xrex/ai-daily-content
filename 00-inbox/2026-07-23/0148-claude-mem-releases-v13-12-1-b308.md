---
id: inbox_999d3b60
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.12.1"
author: "thedotmack"
published_at: 2026-07-23T06:21:49+00:00
fetched_at: 2026-07-24T01:48:46.506554+00:00
content_hash: "b3080ef3b714c8d52b2d1a887f11596d2de1758a7096af43a3e28b0678b2b099"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.12.1

Critical fix: worker restart storm 
 Fixes an infinite worker restart loop triggered by plugin upgrades. The worker-script resolver ranked plugin cache directories by mtime , so when Claude Code stamped a superseded version dir with .orphaned_at (bumping its mtime), every restart respawned the old version while hooks on the new version kept demanding a restart — spawning hundreds of processes until the host machine exhausted its process table. 
 All four resolvers (worker successor, MCP launcher, Codex Windows launcher, POSIX hook prelude) now rank cache dirs by version — never mtime — skip orphan-stamped dirs, and share one deterministic version oracle with the staleness detector ( checkVersionMatch ), making the restart loop structurally impossible. 
 Recommended upgrade for all users. Note: the vulnerable resolver is the one running during an upgrade, so machines are protected from the next upgrade onward. 
 Details: #3371