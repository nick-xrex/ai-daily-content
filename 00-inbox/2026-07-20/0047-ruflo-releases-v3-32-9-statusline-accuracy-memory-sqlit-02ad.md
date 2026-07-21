---
id: inbox_5a02bdca
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.9"
author: "ruvnet"
published_at: 2026-07-20T23:24:35+00:00
fetched_at: 2026-07-21T00:47:12.235825+00:00
content_hash: "02add8d8a390a9a31753eee93caae17185bb25af0b37c5ac89186e4fff3d2734"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.9 — Statusline accuracy + memory/SQLite integrity fixes

Summary 
 Patch release — statusline accuracy + memory/SQLite integrity fixes. 
 Statusline 
 
 #2733 — hooks statusline CLI subcommand hardcoded the model name to 'Opus 4.6 (1M context)' regardless of the actual active model. Now reads it from stdin (matching the generated helper's own behavior), falling back to "Claude Code" — not a fake model name — when stdin has no model field. 
 #2742 — getPkgVersion() in the generated statusline.cjs missed the project install when CWD is a linked git worktree (no local node_modules ), silently falling back to a stale baked-in version. Now walks up from CWD to find the worktree's .git file, resolves the main repo root from its gitdir: pointer, and probes that root's install too. 
 
 Memory / SQLite data integrity 
 
 #2736 — agentdb 's better-sqlite3 floor ( ^11.8.1 ) bundled vulnerable SQLite 3.49.2 (documented WAL-reset bug), coexisting with this repo's own patched 12.9.0 copy in a mixed-engine tree. Deduplicated to a single patched build (12.9.0, SQLite 3.53.0) tree-wide via overrides across all four package.json files, with regenerated lockfiles. 
 #2735 — Memory CRUD's sql.js fallback path silently degraded to a whole-image rename() -over-the-live-file write, which can corrupt a WAL database under a concurrent native writer. Now refuses that unsafe path ( success: false , typed error) when -wal / -shm sidecar files indicate a live native connection, and logs sql.js-fallback demotions instead of failing silently. 
 #2737 — The default doctor run never executed its memory integrity checks — a corrupt database still reported "All checks passed! System is healthy." Wired the real structural/integrity checks into the default run. 
 
 Also fixed during validation 
 
 A WAL-checkpoint-on-close timing race in graph-edge-writer.ts , made newly reproducible on Linux CI by the better-sqlite3 dedup (forcing a single exact build made a previously-masked best-effort checkpoint's timing sensitivity visible). Now forces a blocking wal_checkpoint(TRUNCATE) before close. 
 An npm EOVERRIDE conflict in @claude-flow/cli/package.json between a new direct better-sqlite3 dependency and a self-referential override with a mismatched version spec. 
 
 Test plan 
 
 v3-ci.yml green on main post-merge (all four PRs individually green, plus the merged result) 
 New regression tests: issue-2733-statusline-model-name.test.ts , issue-2742-statusline-worktree-version.test.ts , issue-2735-memory-wal-sidecar-guard.test.ts , doctor-2737-memory-structural.test.ts 
 npm view @claude-flow/cli@latest / claude-flow@latest / ruflo@latest all report 3.32.9 , with latest === alpha === v3alpha on all three packages