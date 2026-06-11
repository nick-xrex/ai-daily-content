---
id: inbox_273cb7c5
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.5.6"
author: "thedotmack"
published_at: 2026-06-11T03:07:33+00:00
fetched_at: 2026-06-11T22:00:27.637401+00:00
content_hash: "4829afe35dad1f29105d0d64241c03876115a177868b34cc1c395eac664b80ce"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.5.6

Worker restart: single source of truth ( #2894 ) 
 This release rearchitects worker lifecycle management to eliminate the restart races behind version-recycle ping-pong storms, EADDRINUSE failures, and "healthy worker reports as not running" lies. 
 Highlights 
 
 Self-replacing worker — on restart, the dying worker spawns its own successor the moment its port frees. Old and new workers never coexist, and nothing external races to spawn into the gap. Hooks wait for the successor and lazy-spawn only as a fallback, at most one recycle per hook event. 
 Restarts prove themselves — worker-service restart now polls /api/health until the pid changes AND the version matches the new build, prints Worker restart verified (pid, version) , and exits 1 on failure instead of reporting success over a dead or stale worker. The daemon's generic start-failure path also exits 1 now. 
 One spawn gate — a wx -flag lockfile ( spawn.lock , 60s mtime staleness, owner-checked release) serializes every external spawn path: hook lazy-spawn, MCP server, and the CLI restart fallback. Lock losers wait for the winner's worker instead of colliding. The two divergent Bun resolvers are unified (closing the kill-then-can't-respawn path), and the MCP server now prefers the marketplace worker script over stale plugin-cache copies. 
 PID file demoted to diagnostics — liveness truth is the port + /api/health . Every PID-file deletion is owner-guarded, so a dying worker can never clobber its successor's file; status reports pid/version/uptime/workerPath from health alone and survives PID-file deletion. 
 First-run fix — settings bootstrap notices now go to stderr, never stdout: the very first hook invocation on a fresh install no longer emits corrupted JSON to the hook framework. 
 Build chain hardened — the dev sync-script's installed-version cache mirror (which wrote new code into old version dirs, manufacturing permanent version disagreement) and its duplicate HTTP restart trigger are deleted; build-and-sync restarts through one verified CLI path. 
 Test hygiene — the test suite can no longer touch the real ~/.claude-mem (a preload tripwire isolates every run), ending sentinel-PID and corrupt-JSON pollution of production state. 
 
 Validation 
 Triple-restart soak (3× consecutive verified restarts, zero duplicate/EADDRINUSE events), plus a live re-creation of the original stale-launcher bug under concurrent session crossfire: one recycle per stale instance, convergence in 16 seconds, zero ping-pong over an 8.5-minute watch. 2,247 tests pass. 
 🤖 Generated with Claude Code