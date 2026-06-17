---
id: inbox_9a0abf2c
date: 2026-06-17
source_ref: "[[00-inbox/2026-06-17/2200-ruflo-releases-v3-12-0-adr-150-metaharness-deep-integra-8966]]"
title: "v3.12.0 — ADR-150 metaharness deep integration"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.12.0
source: ruflo-releases
published_at: 2026-06-17T21:58:28+00:00
fetched_at: 2026-06-17T22:04:18.124005+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.12.0 發布，核心亮點是 ADR-150 深度整合 metaharness 生態系統。新增 10 個 CLI 子命令（score、genome、mcp-scan、threat-model、oia-audit、audit-list、audit-trend、similarity、drift-from-history、mint）、9 個 MCP 工具、1 個 eject CLI、3 個 CI 工作流。採用 4 項架構約束（removable / optional / graceful / CI-gate）確保即使移除所有 metaharness 套件也能保持完整運行。驗證品質經過 130+ 次硬化迭代、117 步煙測套件、120 MCP 執行時斷言。與 3.11.0 完全向後相容，所有套件同步發佈 v3.12.0。"
key_points:
  - "metaharness 深度整合：10 個新 CLI 子命令、9 個 MCP 工具"
  - "4 項架構約束（removable / optional / graceful / CI-gate）確保 metaharness 套件移除後仍可運行"
  - "130+ 驗證硬化迭代、117 步煙測、120 MCP 執行時斷言、94 相似度單元斷言"
tags: [ruflo, metaharness, agent-harness, mcp-tools, architecture]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.12.0 — ADR-150 metaharness deep integration

ruflo v3.12.0 發布，核心亮點是 ADR-150 深度整合 metaharness 生態系統。新增 10 個 CLI 子命令（score、genome、mcp-scan、threat-model、oia-audit、audit-list、audit-trend、similarity、drift-from-history、mint）、9 個 MCP 工具、1 個 eject CLI、3 個 CI 工作流。採用 4 項架構約束（removable / optional / graceful / CI-gate）確保即使移除所有 metaharness 套件也能保持完整運行。驗證品質經過 130+ 次硬化迭代、117 步煙測套件、120 MCP 執行時斷言。與 3.11.0 完全向後相容，所有套件同步發佈 v3.12.0。

### 重點
- metaharness 深度整合：10 個新 CLI 子命令、9 個 MCP 工具
- 4 項架構約束（removable / optional / graceful / CI-gate）確保 metaharness 套件移除後仍可運行
- 130+ 驗證硬化迭代、117 步煙測、120 MCP 執行時斷言、94 相似度單元斷言

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.12.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights 
 ADR-150 deep integration of the metaharness ecosystem as a sibling agent-harness scaffolding system, with 4 architectural constraints (removable / optional / graceful / CI-gate) that keep ruflo fully operational when every @metaharness/* package is removed. 
 New surfaces 
 
 
 
 Surface 
 Count 
 What 
 
 
 
 
 CLI subcommands 
 10 
 npx ruflo metaharness {score,genome,mcp-scan,threat-model,oia-audit,audit-list,audit-trend,similarity,drift-from-history,mint} 
 
 
 Dedicated CLI 
 1 
 npx ruflo eject — lift a ruflo project into a renamed standalone harness 
 
 
 MCP tools 
 9 
 metaharness_score , metaharness_genome , metaharness_mcp_scan , metaharness_threat_model , metaharness_oia_audit , metaharness_audit_list , metaharness_audit_trend , metaharness_similarity , metaharness_drift_from_history 
 
 
 Plugins 
 1 
 plugins/ruflo-metaharness/ 
 
 
 CI workflows 
 3 
 metaharness-ci , no-metaharness-smoke , oia-audit-weekly 
 
 
 
 ADR-152 §3.1 Genome Similarity Search 
 
 Pure-TS, zero @metaharness/* dep 
 Weighted blend: cosine over 9 numerics + categorical over 4 enums + jaccard over agent_topology 
 Returns overall ∈ [0,1] plus per-component breakdown 
 3-tier drift fastpath: slow / --baseline-key ~14× / --baseline-file ~19× 
 
 Bundled fixes 
 
 #2400 — pnpm-lock.yaml regenerated to match @claude-flow/cli specifiers; unblocks main CI 
 #2390 — --version fast-path verified working in 3.11.0+ 
 #1902/#1903/#1904 — Windows shim ruflo-hook.cjs for cost-tracker 
 ADR-125/130 — router env vars registered as known escape hatches 
 ADR-112 — Use when... guidance added to all 9 new MCP tool descriptions 
 
 Routing integration (ADR-148/149) 
 
 @metaharness/router@~0.3.2 wired behind the CLAUDE_FLOW_ROUTER_NEURAL=1 triple-gate 
 SelfEvolvingRouter parallel-logging via CLAUDE_FLOW_ROUTER_PARALLEL_LOG=1 
 3-criteria AND-gate (quality &gt; 2% AND cost &lt; 1% AND latency &lt; 5%) for promotion 
 
 Install 
 npx ruflo@3.12.0 # wrapper (recommended) 
npm i -g ruflo # global install 
 Quality 
 
 130+ iters of validation hardening (lockfile drift, env-var precedence, Windows CI timeouts, pnpm workspace install, topological build, sharp postinstall, fetch-retry on ECONNRESET, eject CLI flag-routing, mcp-scan finding shape normalization, audit-trend chain timeouts, oia-audit graceful degradation, etc.) 
 117-step smoke suite in plugins/ruflo-metaharness/scripts/smoke.sh 
 120 MCP runtime assertions in test-mcp-tools.mjs 
 94 similarity unit assertions in test-similarity.mjs 
 19 cross-reference integrity surfaces anchoring source↔target consistency 
 
 Compatibility 
 
 Backward-compatible with 3.11.0 — no API surface removed 
 Legacy alpha + v3alpha dist-tags continue to point at the latest stable 
 All 3 packages published in lockstep: @claude-flow/cli@3.12.0 , claude-flow@3.12.0 , ruflo@3.12.0 
 
 🤖 Generated with RuFlo

</details>