---
id: inbox_3e624591
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.10"
author: "ruvnet"
published_at: 2026-07-26T22:08:00+00:00
fetched_at: 2026-07-27T01:23:04.182696+00:00
content_hash: "5cda31052ace15a7988e34cde7cedc9feec65eb9a8a399ce0dcdf2dd8587815f"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.10 — tracker-sweep (9 bug fixes + promo seed + follow-ups)

Summary 
 Tracker-fire sweep from the 2026-07-24 → 2026-07-26 window. Ten tracked bugs plus one cold-start regression, landed as six commits on the branch (seventh test-coverage commit incoming). Rebased against origin/main at v3.32.9 — one issue's proposed fix (Codex #2774 ) was based on an incorrect diagnosis and reverted during rebase. 
 Regression check: apples-to-apples fresh-worktree tests — origin/main baseline 98 failed / 3199 total , this branch 91 failed / 3199 total — net -7 failures , zero new failures introduced. 
 Commits 
 
 38f4eaebf — main tracker sweep (9 fixes + promo seed) 
 8933c6c8c — parser.ts:applyDefaults walks command/subcommand options ( #2775 root cause) 
 b2a383079 — memory_store MCP defaults upsert=true for CLI parity ( #2775 ) 
 3abb25823 — CHANGELOG re-scope to 3.32.10 
 4c39225ca — hooks_post-task dual-writes routing decisions to JSON store ( #2786 fix-2) 
 72e6cd705 — 3 parser regression tests for #2775 (52/52 → 55/55) 
 
 Fixed 
 
 Statusline promo row blank on new installs — cold-start local seed pool restored (ADR-311 had emptied it). Cognitum remote pool ( funnel.ruv.io/v1/messages ) remains authoritative via eligibleMessagesFromPools (remote wins by id ); seed only renders during the ≤ 60s cold-start window before first successful remote fetch. Nine seed messages: 1 disclosure, 7 educational tips pointing at cognitum.one docs, 1 promotional. ( v3/@claude-flow/cli/src/funnel/messages.ts ) 
 #2777 — ruflo init no longer imports the entire ruvnet/ruflo repo (97 MB, 384 SKILL.md) into .agents/skills/ruflo/ . Materializes single platform SKILL.md; detects bloated prior install and re-materializes. 
 #2781 — ruflo-adr adr-index no longer silently drops ADR data: status regex accepts - **Status**: proposed ; single-line and wrapped relation lines parse fully; CLI_CORE=1 warns and unifies on @claude-flow/cli@latest . Dry-run over 531 ADRs captures 608 edges cleanly. 
 #2770 — Windows: browser-session MCP tools + two init execFileSync('npx', ...) sites now set shell: process.platform === 'win32' so cmd.exe resolves npx.cmd . POSIX behavior unchanged. 
 #2782 — WorkerDaemon.saveState() + autopilot-state.saveState() + autopilot-state.appendLog() no longer race on shared .tmp filename. All three call writeFileAtomic (pid + timestamp + random-suffixed temp) with try/catch. 
 #2785 — ruflo hooks post-task accepts --task/-t and --store-results flags per CLAUDE.md-documented usage. Routing outcomes finally persist to the namespace hooks_metrics reads. 
 #2786 — AgentDB no longer silently fails to initialize under CLAUDE_FLOW_ENCRYPT_AT_REST=1 . New getAgentDbPath() returns agentdb-memory.db in the same dir as memory.db ; ControllerRegistry (native better-sqlite3) opens a distinct file from the sql.js CRUD writer's encrypted memory.db .
 
 Follow-up #2786 fix-2 : hooks_metrics "Pattern Learning" / "Agent Routing" counters were stuck at zero because the sync reader getIntelligenceStatsFromMemory() reads .claude-flow/memory/store.json while hooks_post-task writes only to AgentDB. Fix: dual-write — after AgentDB write, mirror routing decision into the JSON store with metadata.type: 'routing-decision' . 
 
 
 #2776 — Statusline security segment: STALE / IN_PROGRESS branches reachable via local overlay recomputing freshness on every render from .claude/security-scans/scan-*.json . Env: RUFLO_SCAN_STALE_HOURS (24), RUFLO_SCAN_PENDING_CAP_MIN (30). STALE renders dim gray. 
 #2775 — Memory store to existing key no longer dead-ends. Four layers of fix:
 
 bridgeStoreEntry uses INSERT ... ON CONFLICT with tombstone auto-resurrect; UNIQUE returns typed error instead of null (no more misleading demotion into #2735 guard). 
 bridgeDeleteEntry runs wal_checkpoint(PASSIVE) . 
 parser.ts:applyDefaults walks command + subcommand options (root cause of --upsert default silently dropping — affected every subcommand-declared default, not just this one). 
 memory_store MCP tool schema defaults upsert: true for CLI parity. 
 
 
 
 Investigated / not fixed 
 
 #2774 — Reporter's diagnosis "Codex MCP generator registers management CLI instead of stdio server" appears incorrect: ruflo mcp start IS a working stdio server per v3/@claude-flow/cli/src/commands/mcp.ts ( MCP Server started on stdio ). Upstream d20f1323b fix(codex): ship stable Windows-safe Ruflo integration cleanly centralized the Codex MCP config in mcp-config.ts using the same command shape. A proposed swap to claude-flow-mcp was reverted during rebase. Recommend closing unless a fresh repro against 3.32.9+ is produced. 
 #2786 fix-3 — bridgeRecordFeedback() calls learningSystem.recordFeedback() / .record() and reasoningBank.recordOutcome({taskId, verdict, ...}) with signatures that don't exist on agentdb@3.0.0-alpha.18 's actual API. Wrapped in silent catch. Genuine integration work — needs RL-session lifecycle management across separate CLI processes plus meaningful state/action/reward mapping. Deferred to a separate PR. 
 
 Test plan 
 
 pnpm install at repo root 
 cd v3/@claude-flow/security &amp;&amp; npm run build → tsc + OAuth export verify pass 
 cd v3/@claude-flow/cli &amp;&amp; npm run build → tsc exit 0 
 cd v3/@claude-flow/codex &amp;&amp; npm run build → tsc exit 0 
 CLI test suite on fresh worktree: 91 failed / 3031 passed / 77 skipped / 3199 total — vs origin/main baseline 98 failed / same total. Net -7 failures ; sampled failing tests are WASM/sharp/env issues in files this PR does not touch. 
 Parser tests: 55/55 pass (52 pre-existing + 3 new #2775 regression tests) 
 Windows CI: exercise browser-session MCP tools and init execFileSync npx paths to confirm the shell: process.platform === 'win32' fix. 
 Fresh install smoke: ruflo init in an empty dir, check .agents/skills/ruflo/ is a single ~2KB SKILL.md (not 97MB). 
 Statusline cold-start: on a clean ~/.ruflo/ , first ruflo hooks statusline render shows a promo row from the local seed pool. 
 Encrypt-at-rest: CLAUDE_FLOW_ENCRYPT_AT_REST=1 ruflo memory store ... succeeds and agentdb-memory.db appears next to memory.db . 
 hooks_metrics after several hooks_post-task --store-results calls: "Agent Routing" decision count is non-zero. 
 
 Closes: #2770 #2776 #2777 #2781 #2782 #2785 #2786 (main + fix-2) 
Refs: #2775 (main fix inline + parser root cause + MCP parity) 
Investigation: #2774 (proposed fix reverted; diagnosis appears incorrect against current main) 
Deferred: #2786 fix-3 (agentdb LearningSystem API skew — architectural) 
 🤖 Generated with RuFlo