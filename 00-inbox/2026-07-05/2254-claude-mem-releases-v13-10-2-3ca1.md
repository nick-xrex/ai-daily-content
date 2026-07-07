---
id: inbox_ce51ba39
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.10.2"
author: "thedotmack"
published_at: 2026-07-05T22:47:23+00:00
fetched_at: 2026-07-06T22:54:50.551310+00:00
content_hash: "3ca18a1f6545a9e61cf22e5552183d59ffd5db99633e4fd5bcd4093373a61821"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.10.2

Patch release focused on cross-platform stability and worker/runtime correctness. 
 Fixes 
 
 Worker host : clients now honor CLAUDE_MEM_WORKER_HOST (the address the server actually binds), with IPv6 literals bracketed correctly in health checks and display URLs. 
 Worker identity : cache/marketplace/MCP/CLI/restart launches converge on one worker bundle (stops version-skew from two builds on one port). 
 Windows : centralized spawn shims remove the shell:true footgun; codex hooks emit a Windows-executable command instead of a POSIX-only one. 
 Install : repair now restores the marketplace runtime root (not just the cache); ships the plugin/sqlite runtime modules that were causing MODULE_NOT_FOUND on clean installs. 
 SQLite/settings : atomic settings writes, busy_timeout to avoid SQLITE_BUSY under concurrent worker/hook access, a migration column re-check, and removal of an index create that could crash boot on legacy duplicate rows. 
 Supervisor : preserves HTTPS_PROXY and Bedrock/Vertex skip-auth env for the SDK subprocess. 
 Worktree : relative gitdir: pointers resolved correctly. 
 
 Docs 
 
 New Release Branches guide (main / core-dev / community-edge) with instructions for running the non-stable lines locally. 
 
 Deliberately excluded: client-side observer truncation (kept out per #3096 ) and project-identity re-keying (kept the #2663 repo-root key).