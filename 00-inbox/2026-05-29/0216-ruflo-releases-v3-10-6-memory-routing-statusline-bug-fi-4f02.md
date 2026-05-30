---
id: inbox_e2e76bc7
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.6"
author: "ruvnet"
published_at: 2026-05-29T12:56:04+00:00
fetched_at: 2026-05-30T02:16:29.847679+00:00
content_hash: "4f02f688c4473046889bf0253f279c1f53448489fabdb2045db4178bc28688ee"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.6 — memory, routing & statusline bug fixes (#2219 #2226 #2222 #2221 #2215)

Ruflo v3.10.6 — memory, routing &amp; statusline bug-fix release 
 Five reproducible bugs reported by external contributors ( @pacphi , @casparml , @HF-teamdev ), each verified against source and covered by a regression test. Thanks to all three for the detailed, well-traced reports. 
 🔴 #2219 — Silent write loss on Node 24/26 
 agentdb declares better-sqlite3 as an optional dependency at ^11.8.1 , which has no prebuilt binary for Node 24/25/26. On those runtimes the optional native build fails silently (optional deps never error), and AgentDB drops to a non-persistent backend — stores appear to succeed but never land on disk. 
 Fix: override better-sqlite3 → &gt;=12.8.0 (ships Node 20–26 prebuilds) in both the root umbrella and the ruflo wrapper (root overrides don't propagate to the published wrapper — the #2112 lesson). A new CI guard ( audit-better-sqlite3-override.mjs ) keeps the override pinned so this can't regress. 
 
 If you installed globally on Node 24/26 before this release: npm i -g ruflo@latest restores the native backend. 
 
 🔴 #2226 — agentdb_pattern-store / agentdb_pattern-search never agreed 
 The store and search MCP tools hit disjoint backends , so a stored pattern was never returned by search. Two paths fixed: 
 
 Controller present: bridgeSearchPatterns now reads LocalReasoningBank.findSimilar / getAll — the same backend the store writes to. 
 Controller absent (the common case): the memory-store-fallback search now hydrates each entry's content via getEntry before matching — listEntries returns metadata only (see #2014 ), so the substring scan previously matched nothing. 
 
 🟠 #2222 — route feedback was a no-op 
 Feedback applied the Q-learner update in memory, but the CLI process exits before the autoSaveInterval flush fires, so route-learning never persisted across invocations. Fix: explicit awaited router.saveModel() after feedback. 
 🟡 #2221 — Statusline showed RuFlo V3.6 on global installs 
 getPkgVersion() never probed the global npm root, so npm i -g ruflo fell back to the hard-coded default version. Fix: derive the global node_modules dir from process.execPath (no npm spawn — statusline renders often); covers nvm/mise and Windows layouts. 
 🟡 #2215 — flashAttention reported contradictory state 
 system_info emitted a hard-coded flashAttention: false while hooks_intelligence reported the live probe. Fix: system_info now runs the same getFlashAttention() probe as the authoritative path, so the two tools can't disagree. 
 
 Verification 
 
 New regression suite bug-cluster-2219-2226.test.ts — 5/5 (incl. end-to-end store→search roundtrip) 
 Statusline drift guard — 8/8 (regenerated .cjs byte-identical to generator) 
 tsc clean; CI 29/29 green including the new better-sqlite3 override guard 
 
 Install 
 npm i -g ruflo@latest # or @3.10.6 
npx ruflo@latest --version # → 3.10.6 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) published at 3.10.6 with latest / alpha / v3alpha in lockstep. 
 🤖 Generated with RuFlo