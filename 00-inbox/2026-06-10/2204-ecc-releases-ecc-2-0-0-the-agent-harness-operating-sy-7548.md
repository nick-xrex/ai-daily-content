---
id: inbox_e5ce573e
source: ecc-releases
source_type: rss
url: "https://github.com/affaan-m/ECC/releases/tag/v2.0.0"
author: "affaan-m"
published_at: 2026-06-10T08:56:02+00:00
fetched_at: 2026-06-10T22:04:23.078044+00:00
content_hash: "754895ea6d196142da444be6682cc7d358ae2efee2368ce610ae9c68bbdb292d"
lang: en
caption_quality: None
raw: true
topics: []
---

# ECC 2.0.0 — The Agent Harness Operating System

ECC 2.0.0 — The Agent Harness Operating System 
 ECC 2.0.0 is the stable graduation of the 2.0 line: ECC as a cross-harness operating system for agentic work. Claude Code stays first-class; Codex, OpenCode, Cursor, Gemini, Zed, and terminal-only workflows share the same skills, rules, hooks, MCP conventions, release gates, and operator workflows. This is the months-in-the-making release the rc.1 candidate was building toward. 
 The control pane (early build) 
 
 
 The ECC 2.0 operating surface, running locally ( node scripts/control-pane.js ): operator recall search, live session metrics, a work-items board with ready/running/blocked/done lanes, and an operator column that drives knowledge sync/recall, graph backfill, and the TUI. The session adapters and MCP inventory below feed this board. Build-in-public continues in the Discord #control-pane channel. 
 What is new 
 
 261 public skills across coding, research, security, media, enterprise ops, and agent workflows (rc.1 shipped 243) — plus 64 agents and 84 commands. 
 The control-pane substrate — the foundation of the ECC 2.0 operating surface:
 
 harness-neutral session adapters ( ecc.session.v1 ) covering Claude Code, Codex, OpenCode, and dmux — one schema for "which agent is where, doing what" 
 MCP inventory ( ecc.mcp.v1 ) — one normalized view of every MCP server config across harnesses, with fragmentation/drift detection and secret redaction (it caught a real arg-carried key leak during development) 
 worktree-lifecycle service — deterministic merge-conflict prediction and safe GC for parallel agent worktrees 
 
 
 orch-* orchestrator skill family plus dynamic workflow team orchestration — multi-agent fan-out as a first-class surface. 
 Single-connector MCP default policy — the default set is now exactly one connector ( chrome-devtools ); the other six retired to opt-in after a June 2026 audit. Policy + per-connector rationale: docs/MCP-CONNECTOR-POLICY.md . 
 Rollout-derived optimization pack : parallel-execution-optimizer , benchmark-optimization-loop , data-throughput-accelerator , latency-critical-systems , recursive-decision-ledger . 
 
 Hardening since rc.1 (~30 PRs) 
 
 Plugin hooks were silently no-ops on Node 21+ ( #2184 ) — the hook runner depended on require.main under node -e ; every plugin hook exited cleanly without running. If you are on Node 21+, update now. 
 Windows reliability: CLAUDE_PLUGIN_ROOT normalization ( #2139 ), stdin prompt passing ( #2174 ), symlink/chmod test guards ( #2171 , #2176 ). 
 Security: curl credentials out of argv ( #2175 ), gateguard destructive-checkout gating ( #2158 ) + env knobs ( #2161 ), advisory intake hardening. 
 Correctness: session-end $ -sequence corruption ( #2180 ), project-detect boundary matching ( #2181 ), install manifest gaps ( #2172 ), legacy shim truncation ( #2167 ). 
 Slimmer defaults: smaller OpenCode surface ( #2140 ), rules/zh out of the default install ( #2170 ). 
 
 The ECC Discord is live 
 https://discord.gg/36yGMHGFbR 
 
 #announcements — releases auto-post and pin there (this very release was announced by the workflow shipped in it, #2201 ) 
 #pr-and-issues — live feed of every PR, issue, and release from this repo 
 the ECC bot (built in this release, dependency-free gateway client) answers in-server:
 
 /skill name:&lt;query&gt; — look up any of the 261 skills 
 /docs query:&lt;terms&gt; — search the docs 
 /release — latest release 
 /ecc , /help 
 
 
 #feedback / #feature-requests — read directly by the maintainer; #control-pane — build-in-public on the ECC 2.0 operating surface 
 16 channels, 6 categories, community roles for Contributors, ECC Tools users, and AgentShield users 
 
 Install or upgrade 
 /plugin marketplace add https://github.com/affaan-m/ECC
/plugin install ecc
 
 Existing installs: /plugin update ecc 
 Download 
 
 Release tarball: ecc-universal-2.0.0.tgz (attached below) 
 Full changelog: v2.0.0-rc.1...v2.0.0 
 
 Verification 
 This release passed the full local validation gate before tagging: unicode safety, agent/command/rule/skill/hook validators, install-manifest checks, catalog and command-registry checks, and the complete test suite ( SUITE EXIT: 0 ), plus markdownlint and the pre-push verification gate on every commit. 
 Credits 
 Authored by @affaan-m , built with Claude Code — including this release's Discord community, bot, and announce automation, which shipped themselves end to end.