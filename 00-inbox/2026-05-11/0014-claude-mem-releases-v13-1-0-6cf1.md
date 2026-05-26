---
id: inbox_2c54d38c
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.1.0"
author: "thedotmack"
published_at: 2026-05-11T07:30:39+00:00
fetched_at: 2026-05-26T00:14:50.182762+00:00
content_hash: "6cf147146ac1a4c76eb8865cfcc3203c275b73647e810e21874b8f5633898593"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.1.0

Server-beta event pipeline (phases 4–13) 
 This release lands the full server-beta track developed on server-beta-phase-4-event-pipeline — a self-contained Postgres + BullMQ event-to-observation pipeline with API-key auth, team/project scope, audit log, three AI providers (Anthropic, OpenAI, Google), a dedicated MCP server, legacy compat adapters for existing worker clients, a Docker/Compose stack, and a generation-job retry/cancel surface. 
 Highlights 
 
 Event pipeline : agent_event → observation_generation_jobs (outbox) → BullMQ worker → observation row. Idempotent enqueue, request-id propagation end-to-end, structured audit log. 
 API surface : POST /v1/events , POST /v1/sessions/start , POST /v1/sessions/:id/end , generation-job list/retry/cancel, MCP routes, scoped reads. 
 Legacy compat : /api/sessions/observations and /api/sessions/summarize shims map legacy worker payloads into the new event/job model without touching worker code. Both shims now wrap session lookup in their try/catch so Postgres failures return structured JSON, and resolveServerSession survives TOCTOU races via 23505 catch-and-refetch. 
 POST /v1/sessions/start also catches 23505 on concurrent start with the same externalSessionId and refetches the winning row instead of returning 500. 
 Generation providers : Anthropic, OpenAI, and Google with per-team-project scope enforcement and error classification. 
 Docker / Compose stack and bin/server-beta-cli for local operator workflows. 
 
 Bug fixes 
 
 resolveServerSession Postgres errors no longer escape asyncHandler.catch(next) and return HTML 500s to legacy clients. 
 POST /v1/sessions/start no longer returns 500 to the loser of a concurrent same- externalSessionId race. 
 
 Full PR thread: #2383 .