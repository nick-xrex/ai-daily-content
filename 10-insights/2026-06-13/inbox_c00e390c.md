---
id: inbox_c00e390c
date: 2026-06-13
source_ref: "[[00-inbox/2026-06-13/2200-ruflo-releases-v3-10-46-stale-claude-flow-v3alpha-refer-95b3]]"
title: "v3.10.46 — stale claude-flow@v3alpha references swept (@dskarasev community batch)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.46
source: ruflo-releases
published_at: 2026-06-13T16:57:32+00:00
fetched_at: 2026-06-13T22:05:36.085567+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo 3.10.46 發布補丁版本，清掃 claude-flow → ruflo 重命名後遺留的三處執行時參考。@dskarasev 社群提交的修復集針對無聲失敗問題（使用者.mcp.json 配置仍指向預重命名構建，導致 autopilot/browser/wasm-agent 工具無症狀缺失）；writeMCPConfig 新增舊鍵檢測並提示覆蓋；detectExistingRufloMCP 識別遺留 claude-flow@alpha 鍵防止雙重註冊；swarm.ts 與 ContainerWorkerPool 使用 npx -y ruflo@latest 確保版本一致性。附帶 10 項新測試確保遺留鍵不會再次被引入。"
key_points:
  - "修正三處舊 claude-flow@v3alpha/alpha dist-tag 執行時參考，防止使用者無知情下運行預重命名構建"
  - "writeMCPConfig 新增舊鍵檢測與警告機制，明確提示用戶刪除或 --force 覆蓋 .mcp.json 以恢復 autopilot/browser/wasm-agent 工具"
  - "detectExistingRufloMCP、swarm.ts、ContainerWorkerPool 全面更新至 npx -y ruflo@latest，-y 標誌強制規避本機快取落後版本"
tags: [mcp-integration, migration, claude-ecosystem, configuration-management]
topics: [foundation_models.claude, agents.mcp]
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.46 — stale claude-flow@v3alpha references swept (@dskarasev community batch)

ruflo 3.10.46 發布補丁版本，清掃 claude-flow → ruflo 重命名後遺留的三處執行時參考。@dskarasev 社群提交的修復集針對無聲失敗問題（使用者.mcp.json 配置仍指向預重命名構建，導致 autopilot/browser/wasm-agent 工具無症狀缺失）；writeMCPConfig 新增舊鍵檢測並提示覆蓋；detectExistingRufloMCP 識別遺留 claude-flow@alpha 鍵防止雙重註冊；swarm.ts 與 ContainerWorkerPool 使用 npx -y ruflo@latest 確保版本一致性。附帶 10 項新測試確保遺留鍵不會再次被引入。

### 重點
- 修正三處舊 claude-flow@v3alpha/alpha dist-tag 執行時參考，防止使用者無知情下運行預重命名構建
- writeMCPConfig 新增舊鍵檢測與警告機制，明確提示用戶刪除或 --force 覆蓋 .mcp.json 以恢復 autopilot/browser/wasm-agent 工具
- detectExistingRufloMCP、swarm.ts、ContainerWorkerPool 全面更新至 npx -y ruflo@latest，-y 標誌強制規避本機快取落後版本

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.46)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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

</details>