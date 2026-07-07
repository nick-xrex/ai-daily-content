---
id: inbox_93a123b0
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.25.2"
author: "ruvnet"
published_at: 2026-07-06T02:34:41+00:00
fetched_at: 2026-07-06T22:54:49.632353+00:00
content_hash: "0df0fe749f8ebf38e33fedffa00de175cb3ed2089560a3150e19dd4b1f7cf09e"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.25.2 — AgentDB atomic flushes + backup auto-restore (#2584)

ruflo 3.25.2 — AgentDB durability: atomic flushes + backup auto-restore 
 Fixes #2584 — AgentDB (sql.js) database disk image is malformed under torn/concurrent full-image flushes. 
 
 Atomic DB writes. Every full-image flush now goes temp → fsync → rename (new writeFileAtomic , and writeFileRestricted routed through it), plus the decay-path flush and metrics-db.mjs . A kill/OOM mid-write or a concurrent writer can no longer leave a half-written, malformed image. 
 Backup auto-restore. On a malformed open, when the in-place rebuild can't salvage the image (the reported case where sqlite3 .recover recovered 0 rows), recovery now restores the newest integrity_check=ok snapshot from .swarm/backups/ and parks the corrupt original — turning total loss into automatic recovery. (Rotating periodic backups already existed.) 
 Test: a synthesized torn image (integrity_check fails, rebuild salvages nothing) that must recover via backup-restore — 6/6 pass. 
 
 Additive · fail-closed · zero-regression. npx ruflo@latest . 
 🤖 Generated with RuFlo