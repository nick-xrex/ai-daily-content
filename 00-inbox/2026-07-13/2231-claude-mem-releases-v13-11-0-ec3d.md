---
id: inbox_d75ce0a0
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.11.0"
author: "thedotmack"
published_at: 2026-07-13T04:01:10+00:00
fetched_at: 2026-07-13T22:31:55.334676+00:00
content_hash: "ec3d19eb80cd11340939c5c3bd9a17d12e8020dd83bd937b9657bcfc8c2cf6b6"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.11.0

Worker-native cloud sync (PR #3182 ) 
 The standalone cloud-sync.mjs daemon is retired. The worker now syncs memories itself — every local write nudges a background flusher that drains unsynced rows to cmem.ai, with no separate process to install or babysit. 
 New: 
 
 CloudSync flusher: write-site nudges, 1.5s debounce coalescing write bursts, single-flight flush, 200-row/2MB pages, 30s request timeout, capped exponential backoff on failure 
 GET /api/sync/status — pending counts per kind, last flush time, last error 
 /cloud-sync skill — status checks, first-run credential migration from the legacy .cloud-sync.env , daemon retirement, and worker restart runbook 
 
 Fixed: 
 
 Prompts now join through sdk_sessions to push their real memory_session_id / project instead of an unresolvable fallback — cloud-side prompt-to-session views (Summary ⇄ Prompt toggle, Replay) can now actually find their prompt 
 Schema v40 self-repair: on upgrade, every previously-synced prompt (including ones uploaded by the legacy daemon) is re-queued and re-pushed through the fixed mapper; a backfill lane header suppresses realtime broadcast storms during that re-push 
 Closed a race where a session's memory id registering while its prompt's upload was still in flight could leave that prompt permanently mis-keyed in the cloud — the stamp is now guarded per row and re-pushes with the corrected mapping instead 
 
 Migration: fully automatic and backward compatible. Existing standalone cloud-sync users are migrated on first /cloud-sync run after upgrading; installs with no cloud sync configured are unaffected.