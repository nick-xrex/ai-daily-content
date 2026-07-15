---
id: inbox_28502648
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.30.2"
author: "ruvnet"
published_at: 2026-07-14T20:53:29+00:00
fetched_at: 2026-07-14T22:00:25.083131+00:00
content_hash: "3f40f6fd7dcfeacbeef70207a321fa444923d8ef8ef085e272736cf812522193"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.30.2 — doctor memory functional checks (#2677 checks 1-3)

What 
 Ships @stuinfla 's proposed doctor memory checks 1–3 from #2677 . Bug fix release — no new user-facing surface, no breaking changes. 
 Doctor memory functional checks 
 Before v3.30.2: `ruflo doctor --component memory` was `existsSync` + `statSync` — could not fail on any file that exists. Reported PASS on a 99.97%-empty and even a SQLite-malformed DB per @stuinfla 's 81-store fleet report. 
 After: existence check still runs (unchanged), plus three new checks that layer functional assertions: 
 
 Memory Integrity — opens via sql.js + `PRAGMA integrity_check` 
 Memory Content — &gt;=95% of `memory_entries` rows have non-empty content 
 Memory Embedding Coverage — &gt;=95% of populated rows have a vector 
 
 Each check prints the exact measurement in the message ("content 3/11133 (0.03%)"), fails with a fix-suggestion, and handles the encrypted-DB case as WARN not PASS (per @stuinfla 's "UNKNOWN is never PASS" rule). 
 Also fixed 
 CI env-audit allowlist entries for four escape hatches that were flagging on every PR: 
 
 `RUFLO_AI_BUDGET_DIR` × 3 sites ( #2663 repo-supervisor) 
 `RUFLO_AI_BUDGET_DISABLE` ( #2663 AI-cost fuse) 
 `RUFLO_METAHARNESS_SKIP_LOCAL` (metaharness invoke shim) 
 `RUFLO_HELPERS_LOCKED` (v3.30.0 .LOCKED marker escape hatch) 
 
 Deferred 
 
 Check 4 (recall probe) — needs write+search+delete round-trip through the CLI's memory pipeline; its own PR 
 Checks 5–8 (distillation, reflexion, skills, continuity) + the underlying distill→reflexion write-path fix — @stuinfla 's own PR proposal 
 
 Related 
 
 PR #2681 
 Issue #2677 (still open — checks 4-8 pending) 
 
 Install 
 ```bash 
npx ruflo@latest doctor --component memory 
 or 
 npm install -g @claude-flow/cli@3.30.2 
```