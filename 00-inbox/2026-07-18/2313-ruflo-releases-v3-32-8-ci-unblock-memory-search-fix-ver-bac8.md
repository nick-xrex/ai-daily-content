---
id: inbox_c66d3980
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.8"
author: "ruvnet"
published_at: 2026-07-18T22:31:28+00:00
fetched_at: 2026-07-18T23:13:22.039334+00:00
content_hash: "bac82948716eec4c11c38ba0c0ab79f9a84543f15b5f72a939013f492e868232"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.8 — CI unblock, memory_search fix, version lockstep

v3.32.8 — CI unblock, memory_search fix, version lockstep 
 Fixed 
 
 CI-breaking lockfile drift ( #2719 , #2717 ): v3/pnpm-lock.yaml was pinned to @claude-flow/security@^3.0.0-alpha.10 while package.json had moved to ^3.0.0-alpha.12 , failing every --frozen-lockfile CI job ( Type Check V3 and others) on every PR since the drift landed. Regenerated via pnpm install --lockfile-only . 
 MCP memory_search namespace regression ( #2646 , third occurrence of #1123 / #1131 ): omitting the optional namespace parameter returned 0 results even when data existed across multiple namespaces, because the tool handler coerced an omitted namespace to the literal string 'default' instead of leaving it undefined so the search layer's own namespace || 'all' fallback could fire. Fixed with a regression test that asserts what the tool handler forwards to the search layer directly, so this class of regression is caught at the tool boundary going forward. 
 Package version lockstep (surfaced by #2703 ): claude-flow had drifted to 3.32.2 while @claude-flow/cli / ruflo were at 3.32.7, failing the Plugin package install-safety CI check. All three packages are now back in lockstep at 3.32.8 . 
 
 Verified as already fixed (no code change this release) 
 
 [P0] Worktree daemon fanout quota exhaustion ( #2661 ): confirmed already fixed same-day via #2662 / #2663 (shipped v3.27.4/v3.28.0) — repository-scoped supervisor election, workspace leases, and a global AI-launch budget with a circuit breaker replaced the old per-worktree dedup that let every Git worktree spin up its own set of scheduled Claude-powered workers. The tracking issue had stayed open because the fix commits didn't use GitHub's auto-close keyword; closed now with verification (40/43 tests passing; the 3 failures are a Windows symlink-privilege sandbox limitation, not real bugs). 
 
 Registry 
 
 latest , alpha , and v3alpha dist-tags are synced to 3.32.8 across @claude-flow/cli , claude-flow , and ruflo ( #2703 ). 
 
 Full Changelog : v3.32.7...v3.32.8