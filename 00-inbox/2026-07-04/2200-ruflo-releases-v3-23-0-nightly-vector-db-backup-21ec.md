---
id: inbox_10abdf90
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.23.0"
author: "ruvnet"
published_at: 2026-07-04T21:42:33+00:00
fetched_at: 2026-07-04T22:00:22.947923+00:00
content_hash: "21ecb3cb98812fa759d72f3101ffa2223644b37ae1dd4c74ccdef4c0da722e1d"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.23.0 — nightly vector-DB backup

Nightly vector-memory DB backup 
 
 WAL-safe snapshots of .swarm/memory.db via better-sqlite3's online .backup() — a naive copy of a WAL-mode DB can corrupt; this is consistent + non-destructive (read-only source). 
 Rotation (keep last N, default 7) + optional GCS offsite ( --gcs gs://... / RUFLO_BACKUP_GCS ). 
 memory backup CLI ( --db/--dir/--keep/--gcs ) + a daemon backup worker (24h, enabled by default, opt-out via -w ). 
 
 All backward-compatible. 3-package train at 3.23.0. 
 🤖 Generated with RuFlo