---
id: inbox_0e2a15b4
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.18"
author: "ruvnet"
published_at: 2026-07-27T02:56:19+00:00
fetched_at: 2026-07-27T22:45:54.284215+00:00
content_hash: "b5442cae7b46e2bb6363380eb70b8e46a4be54abebb25ea39a25aa2b10e69405"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.18 — SCM query-intent classifier + routing hints (#2760 dream)

First half of dream-cycle #2760 : query-intent classifier lands, search wires it as an advisory hint; multi-namespace search-backend routing lands in a follow-up when the backend interface exposes an OR filter. 
 Added 
 ruflo memory classify -q "..." — Standalone classifier. Returns intent + confidence + suggested namespaces. --format json for pipelines. 
 ruflo memory search --intent auto|mixed|episodic|semantic|procedural — When non-mixed, prints an SCM router hint with the suggested namespace. Does NOT mutate the search backend in v1 (safety-first — no baseline regression); v2 will apply when the backend adds a multi-namespace OR filter. 
 Namespace map (matches ruflo's actual write conventions): 
 
 episodic → sessions, session-checkpoints, trajectory, routing-outcomes, commands, feedback 
 semantic → patterns, learned-patterns, adr-patterns, adr-edges, reasoning-patterns, concepts 
 procedural → skills, agents, workflow-templates, playbooks, recipes 
 
 Verification 
 
 Regression tests: 7/7 pass (three canonical intents, mixed fallback, explicit override, auto delegation, mixed explicit) 
 E2E: "when did we last touch auth" → episodic (100%); "how does JWT work" → semantic (100%); "how do I onboard a new coder subagent" → procedural (100%); "auth" → mixed (0) 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.18 
 Refs: dream-cycle #2760 (2026-07-22).