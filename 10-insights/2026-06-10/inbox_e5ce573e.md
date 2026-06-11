---
id: inbox_e5ce573e
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_e5ce573e]]"
title: "ECC 2.0.0 — The Agent Harness Operating System"
url: https://github.com/affaan-m/ECC/releases/tag/v2.0.0
source: ecc-releases
published_at: 2026-06-10T08:56:02+00:00
fetched_at: 2026-06-11T00:22:23.758615+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ECC 2.0.0「Agent Harness 作業系統」是跨工具鏈的統一代理平台正式版，支援 Claude Code、Codex、OpenCode、Cursor、Gemini、Zed 等多種 IDE/工具鏈。本版本整合 261 個技能（含編碼、研究、安全、媒體、企業運維、代理工作流）、64 個代理、84 個命令。核心基礎設施包含：(1) 會話規範層 ecc.session.v1 統一代理狀態跨工具鏈，(2) MCP 資源清冊 ecc.mcp.v1 提供單一視圖與祕密編輯，(3) 工作樹生命週期服務預測合併衝突與安全 GC。控制面板提供運維回憶搜尋、實時會話指標、工作板（待辦/執行/受阻/完成）。安全與可靠性增強：修復 Node 21+ hook 執行、Windows symlink 處理、curl 認證祕密、會話末期序列損毀、專案邊界匹配等 30 個 PR。預設 MCP 政策簡化為單一連接器（chrome-devtools），其他 6 個改為選擇加入。Discord 社群已上線，包含技能查詢 bot、即時 PR/issue 動態、反饋頻道。"
key_points:
  - "跨工具鏈統一會話規範 (ecc.session.v1)：單一 schema 統一 Claude Code、Codex、OpenCode、dmux 的代理狀態追蹤"
  - "MCP 資源清冊規範化 (ecc.mcp.v1)：單一視圖檢視所有 MCP 配置，檢測碎片化漂移，自動祕密編輯（開發期間捕獲真實洩露）"
  - "預設安全政策：MCP 預設為拒絕（僅 chrome-devtools），其他 6 個連接器須明確加入（2026 年 6 月審計後改動）"
tags: [agent-harness, multi-harness, mcp, developer-platform, agent-orchestration]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## ECC 2.0.0 — The Agent Harness Operating System

ECC 2.0.0「Agent Harness 作業系統」是跨工具鏈的統一代理平台正式版，支援 Claude Code、Codex、OpenCode、Cursor、Gemini、Zed 等多種 IDE/工具鏈。本版本整合 261 個技能（含編碼、研究、安全、媒體、企業運維、代理工作流）、64 個代理、84 個命令。核心基礎設施包含：(1) 會話規範層 ecc.session.v1 統一代理狀態跨工具鏈，(2) MCP 資源清冊 ecc.mcp.v1 提供單一視圖與祕密編輯，(3) 工作樹生命週期服務預測合併衝突與安全 GC。控制面板提供運維回憶搜尋、實時會話指標、工作板（待辦/執行/受阻/完成）。安全與可靠性增強：修復 Node 21+ hook 執行、Windows symlink 處理、curl 認證祕密、會話末期序列損毀、專案邊界匹配等 30 個 PR。預設 MCP 政策簡化為單一連接器（chrome-devtools），其他 6 個改為選擇加入。Discord 社群已上線，包含技能查詢 bot、即時 PR/issue 動態、反饋頻道。

### 重點
- 跨工具鏈統一會話規範 (ecc.session.v1)：單一 schema 統一 Claude Code、Codex、OpenCode、dmux 的代理狀態追蹤
- MCP 資源清冊規範化 (ecc.mcp.v1)：單一視圖檢視所有 MCP 配置，檢測碎片化漂移，自動祕密編輯（開發期間捕獲真實洩露）
- 預設安全政策：MCP 預設為拒絕（僅 chrome-devtools），其他 6 個連接器須明確加入（2026 年 6 月審計後改動）

**原文：** [ecc-releases](https://github.com/affaan-m/ECC/releases/tag/v2.0.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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

</details>