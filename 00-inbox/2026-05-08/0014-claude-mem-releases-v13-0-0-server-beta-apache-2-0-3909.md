---
id: inbox_71fa0a01
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.0.0"
author: "thedotmack"
published_at: 2026-05-08T08:27:13+00:00
fetched_at: 2026-05-26T00:14:50.185764+00:00
content_hash: "390946d27afbd997e9192d61ee87bc0877e0df52660a4746e8c824ffb3bf7f9e"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.0.0 — Server Beta + Apache 2.0

Highlights 
 This is the claude-mem 13 major release, landing the Server Beta runtime and the project's relicense. 
 Server Beta runtime (opt-in) 
 
 Independent server-beta service with its own lifecycle ( claude-mem server start/status/stop ) 
 Postgres-backed observation storage 
 BullMQ + Redis observation queue engine (gated behind CLAUDE_MEM_QUEUE_ENGINE=bullmq , fail-fast) 
 New /v1 REST API surface (events, sessions, memories, search, context, audit, jobs) 
 API-key auth + Better-Auth proxy 
 Outbox pattern for transactional event-to-job pipelines 
 Generation-job primitives ( ServerJobQueue , ActiveServerBetaQueueManager , deterministic colon-free SHA-256 job IDs) 
 Docker Compose + E2E harness for the new stack 
 
 Licensing 
 
 Repository relicensed from AGPL-3.0 to Apache-2.0 
 NOTICE file added 
 docs/license.md and docs/ip-boundary.md clarify the OSS / commercial boundary 
 ragtime/ subproject also relicensed to Apache-2.0 
 
 Installer 
 
 Server Beta is exposed as an installer option (default off — open-source core is unaffected) 
 
 Migration notes 
 
 Existing users on the worker-era plugin keep working — no breaking changes for the default install 
 Server Beta is opt-in. Worker continues to run on its existing port and SQLite store. 
 See docs/migration-worker-to-server.md for forward-looking migration guidance 
 
 Compatibility 
 
 Node ≥ 20, Bun ≥ 1.0 
 Server Beta requires Postgres + Redis (only when enabled) 
 
 Full diff: v12.7.5...v13.0.0