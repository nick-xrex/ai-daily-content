---
id: inbox_6b6bdc1c
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.12.0"
author: "thedotmack"
published_at: 2026-07-22T23:00:29+00:00
fetched_at: 2026-07-22T23:30:07.253759+00:00
content_hash: "5620e352cc0108e7e2c47987be5bc156913378df6ae6c9d430dc1eefaeb7dbeb"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.12.0

Two-Lane Cloud Sync (cmem.ai Pro) 
 This release ships the complete two-lane sync architecture between your local claude-mem database and the cmem.ai sync hub (PR #3333 ): 
 
 Per-user Durable Object sync hub — a Cloudflare Worker ( workers/sync-hub ) serving isolated HTTP push/pull lanes per user (Phase 1) 
 Client apply path + schema migration v41 — deterministic application of remote changes into the local SQLite store (Phase 2) 
 Hub push/pull transport + mutation outbox — local mutations queue durably and survive offline periods and retries (Phase 3) 
 Advisory WebSocket speed layer — near-real-time sync nudges; correctness never depends on the socket staying up (Phase 4) 
 Guardrails + monitoring — kill switch, watchdog, canary, and a full sync-matrix E2E suite (Phase 5) 
 Canonical v2 projection pipeline and SyncHub-only client cutover 
 Hardened verifier authentication on the sync hub 
 
 Sync is OFF by default. CLAUDE_MEM_CLOUD_SYNC_HUB_URL defaults to empty — nothing leaves your machine unless you configure a hub URL (see the cloud-sync skill or https://docs.claude-mem.ai/cloud-sync ). 
 Fixes 
 
 Restored process-global mock.module cleanup that broke CI under Linux readdir ordering