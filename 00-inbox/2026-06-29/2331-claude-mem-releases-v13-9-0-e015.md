---
id: inbox_2427f799
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.9.0"
author: "thedotmack"
published_at: 2026-06-29T22:28:52+00:00
fetched_at: 2026-07-01T23:31:24.802634+00:00
content_hash: "e0156ad6ca7c481163623733a175ccd5b5b32556f65d81304531708e2d7d97cd"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.9.0

Highlights 
 🚀 New: `claude-mem/sdk` (cmem-sdk) 
 A fully in-process capture → compress → semantic-search pipeline with no HTTP worker and no Redis . Import `createCmemClient` from `claude-mem/sdk`, point it at Postgres + a running `uvx chroma-mcp` + an LLM provider, and call `capture`/`generate`/`search`/`context`/session methods directly. 
 
 New reference docs: CMEM-SDK Reference under SDK &amp; Embedding . 
 Bundle keeps `pg`, `zod`, `@modelcontextprotocol/sdk`, and `@anthropic-ai/sdk` external so consumers resolve them against the installed package. 
 
 ♻️ Server runtime rename 
 `server-beta` → `server` across the runtime, with intentional back-compat aliases for existing settings files. Removed inert `ProviderRegistry`/`EventBroadcaster` boundaries and consolidated the queue resolver. 
 🐛 Fixes 
 
 `generate()`: a provider crash or parse error no longer leaves a job stuck in `processing`; it is transitioned to terminal `failed` with `last_error` recorded before re-throwing. 
 `search()`: empty-query path now reports `chroma: false` (filter-only, not degraded) instead of falsely claiming a Chroma result. 
 CI: the docker e2e job now calls the renamed `e2e:server:docker` script. 
 Docs: corrected `sdk.mdx`'s stale parse-error behavior note. 
 
 Full PR: #3077