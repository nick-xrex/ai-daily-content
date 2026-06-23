---
id: inbox_5985aa28
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.13.1"
author: "ruvnet"
published_at: 2026-06-22T15:51:14+00:00
fetched_at: 2026-06-22T22:03:43.577014+00:00
content_hash: "186c9d56d60660ef31ba3b2d0055429417d4778674eee23faa9e9aa57398f316"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.13.1 — #2432 sql.js MEMFS leak + #2431 graph-edge dual-write corruption

🔧 Bug-fix release 
 #2432 — Unbounded sql.js MEMFS leak (HIGH, ~36 GB observed) 
 `ControllerRegistry.initController()` was calling `controllers.set(name, ...)` without closing the prior instance. `SqlJsRvfBackend` wrappers held an Emscripten MEMFS file (~11 MB each = sizeof `memory.db`) that only releases on explicit `.close()` — JS GC of the wrapper does NOT reclaim MEMFS because the sql.js module is a process singleton. 
 Fix: added `closePriorIfAny(name)` helper, called before every `controllers.set()` site. Best-effort close (catches errors so replacement always proceeds). 
 #2431 — graph-edge-writer dual-write corrupts memory.db (HIGH, ADR-130 regression) 
 `graph-edge-writer.ts` opened sql.js, did in-memory writes, then called `fs.writeFileSync(dbPath, db.export())` after every edge insert. The whole-file flush overwrote `memory.db` while the better-sqlite3 bridge was actively writing through its WAL — the exact dual-write race ADR-068 ( #1257 ) removed. 
 Symptom: `PRAGMA integrity_check` returns `database disk image is malformed (11)` after one `memory_store` + `causal-edge` sequence. 
 Fix: ported from sql.js to better-sqlite3 + WAL mode. Same native engine as the bridge → no whole-file fsync → no race. Public API unchanged. Smoke-tested: 50 concurrent `insertGraphEdge()` calls + `PRAGMA integrity_check` → `ok`. 
 
 Note: this is the minimum-safe fix. The architecturally cleaner fix (route edge writes through the bridge's controller layer per ADR-068) is deferred to a future ADR. 
 
 Distribution 
 
 
 
 Package 
 latest 
 alpha 
 v3alpha 
 
 
 
 
 `@claude-flow/memory` 
 3.0.0-alpha.21 
 3.0.0-alpha.21 
 3.0.0-alpha.21 
 
 
 `@claude-flow/cli` 
 3.13.1 
 3.13.1 
 3.13.1 
 
 
 `claude-flow` 
 3.13.1 
 3.13.1 
 3.13.1 
 
 
 `ruflo` 
 3.13.1 
 3.13.1 
 3.13.1 
 
 
 
 Upgrade 
 ```bash 
npx ruflo@latest # picks up 3.13.1 
npx claude-flow@latest # picks up 3.13.1 
``` 
 Cross-references 
 
 🔗 PR #2444 (this release) 
 🔗 Issue #2432 (MEMFS leak, closed) 
 🔗 Issue #2431 (dual-write corruption, closed) 
 🔗 Companion #2443 (v3.13.0 doctor fix, merged) 
 🔗 Related ADR-068 / ADR-130 (architectural context) 
 
 
 🤖 Generated with RuFlo