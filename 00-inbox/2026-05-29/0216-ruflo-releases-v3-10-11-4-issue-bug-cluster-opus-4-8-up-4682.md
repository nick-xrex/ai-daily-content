---
id: inbox_52150585
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.11"
author: "ruvnet"
published_at: 2026-05-29T22:34:53+00:00
fetched_at: 2026-05-30T02:16:29.843904+00:00
content_hash: "4682b05fa827e1ed06ab88d01e5969c11ad4cba45b45ba6c36b87713b923f01e"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.11 — 4-issue bug cluster (Opus 4.8 + uptime + MCP orphan + Q-encoder)

Fixes four user-reported bugs from the same triage round, each with a regression test: 
 
 #2232 — opus alias bumped to claude-opus-4-8 (with opus-4.7 reachable); executeAgentTask now uses resolveAnthropicModel so literal claude-* ids stop silently downgrading to Sonnet 4.6. 
 #2234 — Parent-death watchdog in ruflo mcp start : exits cleanly when reparented to launchd/init (Claude Code exited). Stops ~50 MB orphans accumulating per restart and a stale orphan winning the stdio handshake. 
 #2235 (B) — system_status.uptime now reads process.uptime() instead of a persisted file timestamp (no more ~8.8-day uptime on a fresh server). Part (A) is upstream in the bundled agentdb package. 
 #2239 — Q-state encoder now mixes all 16 quantized groups via 32-bit FNV-1a (the prior 31-bit fold silently discarded the entire keyword block). encoderVersion=2 bumped in the persisted model; v1 Q-tables auto-reset on load. 
 
 Tests: 17 new regression tests across these four issues; full CLI suite 62 files / 2104 passed / 46 skipped / 0 failed. 
 Install: npx ruflo@3.10.11