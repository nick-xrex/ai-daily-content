---
id: inbox_3d4a322e
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.16.1"
author: "ruvnet"
published_at: 2026-06-29T23:58:55+00:00
fetched_at: 2026-07-01T23:31:23.997047+00:00
content_hash: "90157fc05cbcb3e36c65faba8579c5b3c3bbe1bb78b2fa04761a5f501994ad0c"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.16.1 — fix(daemon): close lockfile race window (#2484)

What's fixed in 3.16.1 
 PATCH bump for issue #2484 — Multiple daemon instances spawned per Claude Code session . EDortta reported 4 identical daemon start --foreground --quiet processes per Claude Code session, accumulating to ~1.7 GB swap on a 16 GB machine with 4 concurrent sessions. 
 Root cause 
 TOCTOU window in the launcher's lockfile dedup. The lock was held for the "is a daemon running?" check but released BEFORE startBackgroundDaemon (which forks the real background process and writes the PID file). Concurrent callers could land in the window between lock-release and PID-file-write, see neither lock nor PID, and each fork their own background daemon. 
 Fix 
 Hold the lock through the entire spawn lifecycle. The lock-loser now ALWAYS sees either a held lock OR a populated PID file — never the empty window. Three explicit release paths (early-return, background, foreground) so every exit path cleans up. 
 Verified 
 
 Build clean ( tsc ) 
 77/77 vitest pass across 3 daemon-related test files 
 6/6 new regression-test cases pass ( daemon-lockfile-race-2484.test.ts ) 
 101/101 CI checks green on PR #2505 before merge 
 
 Install / upgrade 
 npx ruflo@latest # 3.16.1 
npx @claude-flow/cli@latest # 3.16.1 
npx claude-flow@latest # 3.16.1 
 npm dist-tags 
 @claude-flow/cli latest=3.16.1 alpha=3.16.1 v3alpha=3.16.1
claude-flow latest=3.16.1 alpha=3.16.1 v3alpha=3.16.1
ruflo latest=3.16.1 alpha=3.16.1 v3alpha=3.16.1
 
 Related 
 
 PR #2505 — fix(daemon): hold lockfile through spawn lifecycle 
 PR #2506 — chore(release): 3.16.0 → 3.16.1 
 Issue #2484 — Multiple daemon instances spawned per Claude Code session 
 Builds on the lockfile work originally added for #2407 (39 zombie daemons → ~8.5 GiB) — this closes the remaining race window that left the older fix incomplete.