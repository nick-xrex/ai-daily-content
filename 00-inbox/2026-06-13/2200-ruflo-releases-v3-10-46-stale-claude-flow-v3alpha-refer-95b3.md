---
id: inbox_c00e390c
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.46"
author: "ruvnet"
published_at: 2026-06-13T16:57:32+00:00
fetched_at: 2026-06-13T22:00:34.026803+00:00
content_hash: "95b3bf1cb01a42e500275865f96ec49f246742131e2165b5051d69f78fbd5a74"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.46 — stale claude-flow@v3alpha references swept (@dskarasev community batch)

Patch release shipping the @dskarasev community bug batch from PR #2375 — three related runtime references to the deprecated claude-flow@v3alpha (or claude-flow@alpha ) dist-tag that survived the claude-flow → ruflo rename. Each was silently routing users / workers / detection at a pre-rename build that lacks autopilot, browser, wasm-agent, and other current MCP tools. 
 Fixes 
 #2369 — legacy MCP key detection + Scenario A warning 
 Scenario A (the silent-failure mode): if a user's project directory already has an .mcp.json from a pre-rename install, writeMCPConfig was early-returning with a generic skipped message. The user was left with an MCP server pointed at a pre-rename build and zero indication anything was wrong — "autopilot tools missing after init" was the most common downstream symptom. Now : writeMCPConfig parses the existing file, detects stale keys, and surfaces: 
 .mcp.json (existing file uses deprecated key 'claude-flow@alpha' —
autopilot/browser/wasm-agent tools will be missing; delete .mcp.json
and re-run, or re-run with --force to overwrite)
 
 Scenario B (the original report): detectExistingRufloMCP only recognised 'claude-flow' and 'ruflo' as already-registered keys, so a stale claude-flow@alpha entry in a parent directory wasn't detected. Init would walk past it and write a NEW claude-flow -keyed entry — both servers then ran simultaneously under different prefixes ( mcp__claude-flow@alpha__* and mcp__claude-flow__* ), producing duplicate-tool noise. Now : both legacy keys are recognised in both the top-level mcpServers and project-scoped registration paths. 
 #2370 — swarm.ts MCP-down hint 
 swarm_init failure hint changed from: 
 claude mcp add claude-flow npx claude-flow@v3alpha mcp start
 
 to: 
 claude mcp add claude-flow -- npx -y ruflo@latest mcp start
 
 The -- separator avoids claude-mcp flag ambiguity; the -y forces a fresh fetch so npx doesn't pick a stale local install. 
 #2371 — ContainerWorkerPool worker spawn 
 buildWorkerCommand() was returning ['npx', 'claude-flow@v3alpha', 'daemon', 'trigger', ...] . Two problems: the deprecated dist-tag, and the missing -y meaning npx could silently fall back to any locally-installed claude-flow (e.g. 2.7.35) without fetching the published version. Container workers were running pre-rename builds without knowing. Now : ['npx', '-y', 'ruflo@latest', 'daemon', 'trigger', ...] . 
 Tests 
 v3/@claude-flow/cli/__tests__/stale-mcp-key-2369.test.ts — 10 tests pin all three runtime contracts plus a comment-stripped sanity sweep over the entire cli/src/ tree (legitimate legacy-key recognition lists excepted) so a future grep-and-replace can't silently re-introduce the deprecated dist-tag. 
 All 11 existing init-wizard-bugs tests still pass — no regression in the surrounding init paths. 
 Still open from today's triage 
 
 #2373 (HIGH agentic-flow/transport/loader missing from @latest ) — in-repo half already in v3.10.44 (PR #2364 capped the federation plugin peer). Remaining fix is upstream ruvnet/agentic-flow#153 . Commented on the issue. 
 #2372 — user question about the project, not a code bug. 
 
 Install / upgrade 
 npx ruflo@latest init # 3.10.46 
npx @claude-flow/cli@latest # 3.10.46 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) and all three dist-tags ( latest , alpha , v3alpha ) verified at 3.10.46. 
 Diff 
 main...v3.10.45 — PR #2375 plus the release bump. 
 Thanks @dskarasev for the rigorous per-bug write-up with proposed fixes! 
 🤖 Generated with RuFlo