---
id: inbox_a8bb4ffd
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.12.3"
author: "thedotmack"
published_at: 2026-07-23T18:20:07+00:00
fetched_at: 2026-07-24T01:48:46.503117+00:00
content_hash: "dadda33485eb3f5b123066204b1d1df4428bad4ee30f50e2f0ff99c207be6d77"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.12.3

Hotfix: self-perpetuating stale-worker recycle loop ( #3378 ) 
 The bug. On a version mismatch, hooks asked the running (stale) worker to restart itself — and the dying worker spawned its successor using its own install's code and resolver. A ≤13.11.0 worker would respawn its own version, re-bind the worker port before the hook's correctly-resolved lazy-spawn could, and the mismatch recurred on every prompt, forever. One report measured 2,424 recycles in a single day , with every UserPromptSubmit ending in a ~40s hook timeout. Because the buggy handoff ran inside the old install's process, fixing the new version's resolver alone could never break the loop. 
 The fix. Hooks no longer delegate the recycle to the corpse. On version mismatch the hook now: 
 
 reads the owner-verified worker PID file, 
 SIGKILL s the stale worker — the only teardown guaranteed to execute zero stale-version code, 
 waits for the port to actually close, and 
 spawns the resolved installed version itself, via the existing lazy-spawn path and the single version oracle. 
 
 The dying-worker successor handoff now serves only CLI-initiated claude-mem restart , where the running install is the resolved install. 
 If you're currently stuck in the loop: just update. The first hook that runs after this version installs will kill the resident stale worker and take over — no manual cleanup needed. 
 Not addressed in this release (still open): the FOREIGN KEY constraint failed background-init error also reported in #3378 , and the Windows stale-socket port hold in #3380 .