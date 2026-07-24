---
id: inbox_915689c5
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.12.4"
author: "thedotmack"
published_at: 2026-07-23T22:47:26+00:00
fetched_at: 2026-07-24T01:48:46.497233+00:00
content_hash: "df94ca25525396f66ca4368e8a0f5c1d6995e9ccc7e81596279da58831d7a1ad"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.12.4

Four root-cause fixes from the post-v13.12.2 issue batch. 
 Fixes 
 Shutdown teardown no longer skipped on a non-listening server handle ( #3380 ) 
 performGracefulShutdown treated Node's ERR_SERVER_NOT_RUNNING from server.close() as fatal in step 1, which skipped session drain, MCP close, Chroma stop, DB close, and supervisor stop — the Windows port-hold symptom. An already-closed server now counts as closed (explicit code check, everything else still rejects), and Server.listen() assigns the handle only once actually listening, so a failed bind can no longer leave a stale non-listening handle for shutdown to trip on. ( #3387 ) 
 Concept tags participate in context injection again ( #3379 ) 
 The observer prompt's own guidance format taught the model to emit keyword: description concept tags, which the exact-match injection SQL silently excluded — observations tagged that way never surfaced. Concepts are now truncated at the first colon at the parse boundary, the producer prompts in all four modes require bare keywords, and migration v49 backfills stored rows — requeueing corrected native rows for cloud re-push (sync_rev bump + synced_at reset, mirroring the prompt-repair convention) and guarded by json_valid so a malformed row cannot abort boot. The injection query itself is unchanged. ( #3389 ) 
 Background init no longer aborts on orphaned rows; adoption race and logging fixed ( #3378 ) 
 The v7/v9 table-rebuild migrations copy child tables with foreign keys enforced, so historical orphaned observations/summaries (no sdk_sessions parent) threw FOREIGN KEY constraint failed in the SessionStore constructor and the worker never reported ready. A pin-down test proved the site red→green; the fix repairs stub parents in-place before both rebuild copies — orphaned rows are user data and are never deleted. Also: adoption errors now log as real text instead of [object Object] , and the worktree-adoption kick moved after DB init so its write connection no longer races boot migrations ( database is locked ). Complements the stale-worker recycle fix shipped in 13.12.3. ( #3390 ) 
 Maintainer directives no longer ship to end users ( #3381 ) 
 Root CLAUDE.md's Local Status Notes and Daily Maintenance sections — including an autonomous upgrade-and-commit directive — shipped verbatim to every marketplace git-clone install and were obeyed by end-user Claude instances (the #2537 .npmignore guard only covers the npm tarball, see #3359 ). Those sections now live in gitignored CLAUDE.local.md ; tracked CLAUDE.md keeps only contributor content, and the maintainer sync copies the slim file over any stale marketplace copy. ( #3391 ) 
 Verification 
 Full suite 2539 pass / 0 fail, tsc clean, anti-pattern sweep over the round's diff clean, worker restart cycle at 13.12.4 shows none of the fixed failure signatures.