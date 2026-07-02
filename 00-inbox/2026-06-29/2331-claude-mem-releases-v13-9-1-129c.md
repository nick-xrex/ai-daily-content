---
id: inbox_0deb9cd4
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.9.1"
author: "thedotmack"
published_at: 2026-06-29T23:47:48+00:00
fetched_at: 2026-07-01T23:31:24.800381+00:00
content_hash: "129caf8eb2949b9edb19e3b6e7c54261120fee4d5cfad95b73cea20df1ea33e3"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.9.1

What's Changed 
 Patch release shipping the platform-source recovery work merged in #3088 , plus dependency and Codex hardening. 
 Fixes 
 
 codex: load startup context through MCP, with HTTP fallback to the worker 
 codex: avoid shell spawning the Codex installer 
 recovery: scope memories by platform source 
 observer: drop invalid prose and pause on quota 
 chroma: prewarm uvx and harden shutdown 
 deps: surface dependency-health preflight and degrade gracefully when CLI deps are missing 
 telemetry: replace Bun UUIDv5 dependency 
 
 Tests 
 
 Stabilize session init after the server rename 
 Restore Chroma MCP mock to prevent cross-suite leakage 
 
 Full Changelog : v13.9.0...v13.9.1