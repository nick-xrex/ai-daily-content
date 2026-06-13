---
id: inbox_32ec2d03
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.43"
author: "ruvnet"
published_at: 2026-06-12T14:58:21+00:00
fetched_at: 2026-06-13T03:36:12.951403+00:00
content_hash: "1b10c9f1c060105a68901f537e2209d278bdf581c508ba9ff0d0cb0badc1f9ef"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.43 — Fable 5 / Opus 4.x temperature fix, daemon TTL, federation cap

Patch release bundling four bug fixes landed since 3.10.42. 
 Fixes 
 #2358 — agent_execute 400s every current frontier Anthropic model (HIGH) 
 callAnthropicMessages() always sent temperature (default 0.7), but Fable 5, Opus 4.8, and Opus 4.7 removed temperature / top_p / top_k . Every request returned 400 invalid_request_error: temperature: Extra inputs are not permitted . Invisible on Claude-Max (no key → provider check short-circuits before fetch); fatal on a raw ANTHROPIC_API_KEY . New modelRejectsSamplingParams(model) predicate gates the field; Sonnet 4.6 / Haiku 4.5 / Opus ≤ 4.6 unchanged. Closes #2357 Finding A. (HF-teamdev — first-time contributor, thank you for the file:line-cited finding map.) 
 #2365 — OpenRouter slugs refreshed to current 4.x family 
 The OpenAI-compat path still referenced the Oct-2025 retired model IDs: 
 
 default model: anthropic/claude-3.5-sonnet → anthropic/claude-sonnet-4-6 
 haiku alias: anthropic/claude-3.5-haiku → anthropic/claude-haiku-4-5 
 sonnet / inherit alias: anthropic/claude-3.5-sonnet → anthropic/claude-sonnet-4-6 
 opus alias: anthropic/claude-3-opus → anthropic/claude-opus-4-8 
 
 OPENROUTER_DEFAULT_MODEL still wins for callers who want to pin a specific slug. Closes #2357 Finding C. 
 #2361 — daemon self-terminating TTL + global status + HNSW/init footguns 
 Community PR by @shaal addressing @pacphi 's ruflo-machine-ref investigation. The daemon used to run interval workers (audit ~30m, optimize/testgaps ~60m, ...) forever, each spawning a headless claude --print sweep. Audited evidence traced a Max-plan quota burned in 1–2 days to 6 immortal daemons (oldest 19 days) and a recurrence to 17 per-project daemons (34,533 total worker runs — ~94% of token spend was background machinery). This release adds: self-terminating TTL, idle shutdown, daemon status --all (global, not just current workspace), honest HNSW reporting, init footgun guards. Closes #2360 . 
 #2364 — federation plugin: cap agentic-flow peer to &lt;2.0.13 
 Upstream agentic-flow@2.0.13 dropped the ./transport/loader subpath. Runtime impact was bounded — midstream-aware-loader.ts wraps the dynamic import in try/catch and falls back to midstream-native — but the peer range previously said &gt;=2.0.12-fix.8 and silently accepted 2.0.13. Tightened to &gt;=2.0.12-fix.8 &lt;2.0.13 so npm install warns about the incompat instead of hiding it behind a silent fallback. 
 Still open from #2357 
 
 Finding B (Fable routing tier RFC, PR #2359 ) — behavior-neutral, 21/21 tests green, awaiting maintainer decision before the June 22 Max-plan API-credits window. Review comment on the PR lays out the three design calls. 
 
 Install / upgrade 
 npx ruflo@latest init # 3.10.43 
npx @claude-flow/cli@latest # 3.10.43 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) and all three dist-tags ( latest , alpha , v3alpha ) verified at 3.10.43. 
 Diff 
 main...v3.10.42 — PRs #2358 , #2361 , #2364 , #2365 plus the release bump. 
 🤖 Generated with RuFlo