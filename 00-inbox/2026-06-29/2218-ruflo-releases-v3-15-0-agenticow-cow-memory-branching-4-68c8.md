---
id: inbox_8a4555e2
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.15.0"
author: "ruvnet"
published_at: 2026-06-29T16:05:08+00:00
fetched_at: 2026-06-29T22:18:27.190775+00:00
content_hash: "68c8de89e013b1b81a81fe1a463323e33eaf5614bad3af5beaf2b0d1b5ba279c"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.15.0 — agenticow COW memory branching (4 MCP tools, +162-byte branches)

What's new in 3.15.0 
 This is a MINOR release adding agenticow@~0.2.3 — Copy-On-Write memory branching — as 4 new MCP tools. No breaking changes; the new dep is in optionalDependencies with graceful-degraded fallbacks. 
 New MCP tools (4) 
 
 
 
 Tool 
 Purpose 
 
 
 
 
 agenticow_branch 
 COW-fork a base .rvf memory at ~162 bytes regardless of base size 
 
 
 agenticow_checkpoint 
 Freeze a labelled restore point that survives close+reopen 
 
 
 agenticow_rollback 
 Discard edits since the most recent checkpoint, O(edits) not O(N) 
 
 
 agenticow_promote 
 Atomically merge a branch's edits (with tombstones) into a base or target 
 
 
 
 Read-through semantics on every branch: parent ∪ edits, child wins . Persisted via &lt;file&gt;.agenticow.json lineage manifest. 
 Motivation 
 v3.14.4 uncovered a 3.3 GB tarball-bloat regression where Darwin loops' git-worktree-per-agent pattern accumulated full-copy snapshots. agenticow is the structural fix — 162-byte branches instead of full copies. 
 Measured perf vs. published claims 
 Full bench harness: scripts/bench-agenticow.mjs 
Findings doc: docs/agenticow/findings.md ( gist mirror ) 
 
 
 
 Claim 
 Result 
 Detail 
 
 
 
 
 162-byte branches 
 ✅ Confirmed exact 
 Constant at N=1k, 10k, 50k 
 
 
 ≥3,000× smaller than full-copy 
 ✅ Confirmed and exceeded 
 3,214× at N=1k → 181,930× at N=50k 
 
 
 "0.5ms branch" 
 ❌ Not reproduced 
 Measured ~10 ms (fixed cost, not size-proportional) 
 
 
 "83× faster" 
 ❌ Crossover N≈30k 
 Below crossover, full-copy wins 
 
 
 
 We measured, not parroted — per CLAUDE.md's source-of-truth rule. 
 Architectural constraint (zero hard runtime dep) 
 agenticow is in optionalDependencies . When missing, every tool returns {success: true, degraded: true, reason: 'agenticow-not-found'} and exits 0. Same posture as the metaharness integration (ADR-150). Verified by the no-metaharness-smoke CI gate on every PR. 
 What this enables in ruflo 
 
 Darwin loops without worktree bloat — branch-per-iteration at 162 B instead of full git-worktree clones 
 Speculative agent edits with O(1) rollback — checkpoint → try → rollback if the JUDGE step rejects 
 Per-user / per-session memory personalization — federation primitive for fork-and-merge 
 A/B routing experiments on real memory — branch candidate routers, bench each, promote the winner 
 
 Tests 
 
 7/7 vitest unit tests pass ( v3/@claude-flow/cli/__tests__/agenticow-tools.test.ts ) 
 8/8 bash smoke contract pass ( scripts/smoke-agenticow.sh ) 
 108/108 CI checks green on PR #2500 before merge 
 
 Install / upgrade 
 npx ruflo@latest # 3.15.0 
npx @claude-flow/cli@latest # 3.15.0 
npx claude-flow@latest # 3.15.0 
 Or via package.json : 
 {
 "dependencies" : {
 "@claude-flow/cli" : " ^3.15.0 " 
 }
} 
 Verified npm dist-tags 
 @claude-flow/cli latest=3.15.0 alpha=3.15.0 v3alpha=3.15.0
claude-flow latest=3.15.0 alpha=3.15.0 v3alpha=3.15.0
ruflo latest=3.15.0 alpha=3.15.0 v3alpha=3.15.0
 
 Related 
 
 PR #2500 — feat(mcp): integrate agenticow@~0.2.3 — COW memory branching (4 MCP tools) 
 PR #2501 — chore(release): 3.14.4 → 3.15.0