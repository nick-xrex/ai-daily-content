---
id: inbox_9240af3b
date: 2026-06-19
source_ref: "[[00-inbox/2026-06-19/2200-repowise-releases-v0-21-0-59fc]]"
title: "v0.21.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.21.0
source: repowise-releases
published_at: 2026-06-19T16:01:48+00:00
fetched_at: 2026-06-25T22:06:10.302767+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.21.0 發布「工作空間架構智能」版本。新增跨倉庫系統圖、服務粒度契約提取與診斷、架構一致性檢查、相依性循環偵測與 breaking-change 防護。擴展多框架 HTTP 提取：Rust reqwest、C#/Unity HTTP consumers、JS 包裝器與變數 URL consumers，新增 gRPC context 防護。引入工作空間架構指標：傳播成本（propagation cost）、core-periphery 角色分析、composite 架構評分（1-10 分制），用於識別高風險倉庫。Cross-repo blast radius 與 change risk 分析。MCP tool 表面可配置、context-aware、支援從儀表板編輯 MCP 工具集。"
key_points:
  - "cross-repo 系統圖與服務粒度提取，支援 breaking-change 防護與 blast radius 分析，識別變更範圍"
  - "架構指標：propagation cost（傳播成本）、core-periphery 角色、composite 架構評分（1-10），量化架構風險"
  - "MCP tool 表面動態化：context-aware 選擇工具、支援從 Web UI 編輯 MCP 工具集，適應不同團隊需求"
tags: [workspace-architecture, system-graph, breaking-change-guard, architecture-metrics]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.21.0

Repowise v0.21.0 發布「工作空間架構智能」版本。新增跨倉庫系統圖、服務粒度契約提取與診斷、架構一致性檢查、相依性循環偵測與 breaking-change 防護。擴展多框架 HTTP 提取：Rust reqwest、C#/Unity HTTP consumers、JS 包裝器與變數 URL consumers，新增 gRPC context 防護。引入工作空間架構指標：傳播成本（propagation cost）、core-periphery 角色分析、composite 架構評分（1-10 分制），用於識別高風險倉庫。Cross-repo blast radius 與 change risk 分析。MCP tool 表面可配置、context-aware、支援從儀表板編輯 MCP 工具集。

### 重點
- cross-repo 系統圖與服務粒度提取，支援 breaking-change 防護與 blast radius 分析，識別變更範圍
- 架構指標：propagation cost（傳播成本）、core-periphery 角色、composite 架構評分（1-10），量化架構風險
- MCP tool 表面動態化：context-aware 選擇工具、支援從 Web UI 編輯 MCP 工具集，適應不同團隊需求

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.21.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's Changed 
 
 feat(overview): rebuild repo overview around code health by @RaghavChamadiya in #501 
 feat(coupling): repo-wide change-coupling graph by @RaghavChamadiya in #497 
 UX overhaul: airier, diagram-first web UI on a shared composition backbone by @swati510 in #504 
 fix(ingestion): skip Unity-generated .NET scan paths by @joptimus in #499 
 refactor(workspace): split contract extractors into per-framework dialects by @RaghavChamadiya in #505 
 feat(workspace): extract Rust HTTP route providers by @RaghavChamadiya in #506 
 feat(workspace): extract C#/Unity HTTP consumers by @RaghavChamadiya in #507 
 feat(workspace): follow JS wrapper and variable-URL HTTP consumers by @RaghavChamadiya in #508 
 fix(workspace): require gRPC context for C# client consumer extraction by @RaghavChamadiya in #509 
 feat(workspace): extract Rust reqwest HTTP consumers by @RaghavChamadiya in #510 
 feat(workspace): service-granular system graph and extraction diagnostics by @RaghavChamadiya in #511 
 feat(workspace): live system map for cross-repo services by @RaghavChamadiya in #512 
 Cross-repo blast radius and change risk by @RaghavChamadiya in #513 
 Breaking-change guard for cross-repo contracts by @RaghavChamadiya in #514 
 Workspace architecture conformance, dependency cycles, and DSM view by @RaghavChamadiya in #515 
 fix(workspace): stop contract extraction scanning nested repos (1M-file hang) by @RaghavChamadiya in #516 
 Workspace architecture metrics: propagation cost, core-periphery roles, and a 1-10 score by @RaghavChamadiya in #517 
 Consolidate the MCP tool surface and reconcile tool-count docs by @RaghavChamadiya in #519 
 Make the MCP tool surface context-aware and configurable by @RaghavChamadiya in #520 
 Edit the MCP tool surface from the dashboard by @RaghavChamadiya in #521 
 release: v0.21.0 — workspace architecture intelligence + configurable MCP surface by @RaghavChamadiya in #522 
 
 Full Changelog : v0.20.0...v0.21.0

</details>