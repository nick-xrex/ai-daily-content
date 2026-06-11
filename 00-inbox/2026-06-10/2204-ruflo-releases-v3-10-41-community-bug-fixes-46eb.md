---
id: inbox_f1254aab
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.41"
author: "ruvnet"
published_at: 2026-06-10T15:48:22+00:00
fetched_at: 2026-06-10T22:04:24.695293+00:00
content_hash: "46eb84354a76ec99772521fefab3dc97410ecdbdd7795ef457e6be08f4a3c643"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.41 — community bug fixes

Three community bug fixes plus the ADR-147 nested-subagent infrastructure landed since v3.10.40. PATCH bump — no API breaks. 
 Community bug fixes (PR #2346 ) 
 fix(statusline) : resolve installed CLI bin + bump cache TTL 10s→60s ( #2337 ) 
 Thanks @shaal for the detailed report with %CPU measurements. The statusline was calling npx --yes @claude-flow/cli@latest hooks statusline --json on every render — the @latest tag forced npm registry re-resolution per call. With ~6 concurrent sessions on a 12-core box: load average 40-65, each npm exec consuming 55-90% of a core. 
 Fix: new resolveCliBin() finds an installed bin/cli.js (project / monorepo / plugin marketplace / global node_modules — covers ~/.npm-global and similar custom-prefix layouts) and invokes it via process.execPath directly. Falls back to npx --prefer-offline @claude-flow/cli (no @latest ) when nothing's installed. Cache TTL 10s→60s. Applied to both the dogfood helper and the ruflo init generator template. 
 fix(hive-mind) : await spawned claude before returning ( #2297 ) 
 Thanks @clement-livdeo for the XTVERSION-on-prompt diagnostic — that single string nailed the root cause: the parent process exited immediately after spawn, the child claude lost its controlling terminal mid-init, and the terminal's capability-query response leaked onto the next shell prompt. 
 Fix: spawnClaudeCodeInstance() now awaits the child's exit (or error) before returning. The existing claudeProcess.on('exit', ...) log lines actually print now, and the non-interactive ( -p / --non-interactive ) path completes only after Claude Code does. 
 fix(session) : atomic writes to current.json + corrupted-file self-heal ( #2307 ) 
 Thanks @BIWizzard for the diff — same class as #1707 / #1637 which were fixed elsewhere with atomic writes; session.js was missed in that sweep. Per-fd-offset semantics in writeFileSync meant a shorter payload could overwrite the start of a longer one without shrinking the file, leaving the longer payload's tail dangling past the end (valid JSON + trailing garbage). 
 Fix: all 5 session-file writes go through a new atomicWrite() (temp file + rename() ). restore() wraps JSON.parse in try/catch so existing corrupt files self-heal by starting a fresh session instead of throwing. 
 Infrastructure 
 ADR-147 — nested subagent depth=5 integration (PR #2336 ) 
 Captures Boris Cherny's nested-subagent announcement with full empirical block, the ruflo agent files (8 new agents + 1 skill) that opt into nested spawning via tools: [Task, ...] , P2 stage 1 (CLI flags + MCP schema for capturing parent_agent_id in the post-task hook), and a regression probe in scripts/probe-nested-spawn-depth.mjs . 
 Empirically determined: declaring tools: [Task] in YAML is necessary but not sufficient in CLI 2.1.169 — the runtime applies a hardcoded denylist that strips Task at parent→child spawn time. Documented in the ADR with the spawn-tree the day the upstream denylist lifts. 
 Security baseline (PR #2340 ) 
 docs/security/socket-baseline.md documents every category in the Socket.dev alert page for claude-flow@3.10.40 — what's protected by root overrides , what's not cleanly fixable from inside claude-flow (consumer-side npm overrides only apply at the dep-tree root), what's inherent to a CLI agent platform (filesystem/network/shell access etc.), and the false positives (Socket's "did you mean z-schema?" suggestion against zod ). Also removes the broken pages.yml workflow that had failed 10+ consecutive runs. 
 Open follow-ups from the same triage pass 
 
 #2305 — embedding model/dimension ignored at runtime (architectural; awaiting reporter's config-chain design as PR) 
 #2296 — 7 controllers null from version skew between @claude-flow/memory@3.0.0-alpha.19 and agentdb@3.0.0-alpha.16 (needs coordinated package republish) 
 
 Install 
 npx ruflo@latest
 # or 
npx claude-flow@latest
 # or 
npm install @claude-flow/cli@latest 
 All three packages at 3.10.41 across all dist-tags (latest, alpha, v3alpha). 
 🤖 Generated with RuFlo