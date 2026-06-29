---
id: inbox_323bc16d
date: 2026-06-06
source_ref: "[[00-inbox/.../inbox_323bc16d]]"
title: "v0.17.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.17.0
source: repowise-releases
published_at: 2026-06-06T14:32:01+00:00
fetched_at: 2026-06-29T02:00:52.047490+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.17.0 釋出多項核心功能：新增 Claude Code 外掛與根目錄 Marketplace 集成；推出 Distill 功能（索引感知的輸出蒸餾引擎，支援 distill/expand/saved 模式）；實現多語言 import 解析與精選知識圖譜引擎；在 git indexer 中加入 agent-provenance 層以追蹤來源；改進健康度指標計算（針對小型團隊與低活躍倉庫的熱點、所有權風險校準）；性能優化包括增量更新隨變更規模擴展、解析與 betweenness 的跨增量更新快取；UI 改善（主題系統、星座圖、C4 藍圖畫布）；強化 MCP get_context 邊界處理與批次隔離；修復檔案系統掃描以避免巢狀倉庫，並新增 30+ 項錯誤修復與改進。"
key_points:
  - "Distill 引擎：索引感知的輸出蒸餾、擴展與保存模式，搭配 PowerShell hook 涵蓋與 Grep 救援機制"
  - "多語言導入解析 + 精選知識圖譜：以 38 倉庫矩陣驗證，支援 Python/JS/Kotlin/Django/Spring 等框架的跨語言依賴追蹤"
  - "性能：增量更新隨變更大小擴展、跨更新快取解析與 betweenness、已索引倉庫路由至增量路徑避免重新掃描"
tags: [repowise, distill-engine, multi-language-resolution, mcp-hardening, knowledge-graph]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.17.0

Repowise v0.17.0 釋出多項核心功能：新增 Claude Code 外掛與根目錄 Marketplace 集成；推出 Distill 功能（索引感知的輸出蒸餾引擎，支援 distill/expand/saved 模式）；實現多語言 import 解析與精選知識圖譜引擎；在 git indexer 中加入 agent-provenance 層以追蹤來源；改進健康度指標計算（針對小型團隊與低活躍倉庫的熱點、所有權風險校準）；性能優化包括增量更新隨變更規模擴展、解析與 betweenness 的跨增量更新快取；UI 改善（主題系統、星座圖、C4 藍圖畫布）；強化 MCP get_context 邊界處理與批次隔離；修復檔案系統掃描以避免巢狀倉庫，並新增 30+ 項錯誤修復與改進。

### 重點
- Distill 引擎：索引感知的輸出蒸餾、擴展與保存模式，搭配 PowerShell hook 涵蓋與 Grep 救援機制
- 多語言導入解析 + 精選知識圖譜：以 38 倉庫矩陣驗證，支援 Python/JS/Kotlin/Django/Spring 等框架的跨語言依賴追蹤
- 性能：增量更新隨變更大小擴展、跨更新快取解析與 betweenness、已索引倉庫路由至增量路徑避免重新掃描

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.17.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.17.0

What's Changed 
 
 feat(plugin): Claude Code plugin + root marketplace, refreshed to current surface by @RaghavChamadiya in #356 
 fix(health): calibrate hotspot + ownership risk for small teams and quiet repos by @RaghavChamadiya in #363 
 fix(web): decode breadcrumb path labels by @joptimus in #359 
 fix(server): honor exclude_patterns in server jobs; prune stale rows by @joptimus in #354 
 fix(generation): close never-started page coroutines on Ctrl+C abort by @RaghavChamadiya in #365 
 feat(cli): owl mascot init banner with repo-seeded heatmap wordmark by @swati510 in #364 
 feat(git): agent-provenance layer in the git indexer by @RaghavChamadiya in #366 
 perf: make indexing &amp; incremental update scale with change size by @RaghavChamadiya in #368 
 perf: cache parsing and betweenness across incremental updates by @RaghavChamadiya in #369 
 feat: Distill - index-aware output distillation (distill / expand / saved) by @RaghavChamadiya in #378 
 feat(init): clearer mode panel + searchable model selection by @RaghavChamadiya in #379 
 fix(core): pruned filesystem walks — stop scanning nested repos and junk trees by @RaghavChamadiya in #380 
 fix: honor include-submodules across incremental updates and upgrades by @RaghavChamadiya in #381 
 fix(init): record the distill rewrite-hook verdict in every flow by @RaghavChamadiya in #382 
 perf(workspace): route already-indexed repos through the incremental update path by @RaghavChamadiya in #384 
 fix(ingestion): resolve explicit relative JS imports by @nkgotcode in #376 
 fix(analysis): honor persisted submodule flags in health and dead-code by @RaghavChamadiya in #383 
 fix: process hygiene - MCP orphan watchdog, live-PID update locks, PATH-hijack-proof registration by @RaghavChamadiya in #385 
 build(deps): bump starlette from 0.52.1 to 1.0.1 by @dependabot [bot] in #367 
 fix(health): use whole-file NLOC for health file metrics by @joptimus in #387 
 fix(ingestion): rescue local Express route middleware from unused-export detection by @joptimus in #386 
 fix(health): compute duplication_pct from the union of clone ranges by @RaghavChamadiya in #388 
 fix(distill): Grep-rescue correctness, PowerShell hook coverage, nudge floor, allowlist seeding by @RaghavChamadiya in #389 
 feat(distill): lint filter, missed-savings discovery, per-surface ledger tagging by @RaghavChamadiya in #390 
 feat(distill): Codex CLI rewrite support + repowise corrections by @RaghavChamadiya in #391 
 feat(ui,web): theme system, constellation graph, blueprint C4 canvas, web app adoption by @swati510 in #405 
 feat(tools): knowledge-graph validation harness with pinned 38-repo matrix by @swati510 in #404 
 fix(mcp): harden get_context — segment-boundary partial match, git-file fall-through, batch isolation by @swati510 in #401 
 feat(kg)!: multi-language resolution, curated knowledge-graph engine, curated wiki modules by default by @swati510 in #392 
 feat(distill): default the init rewrite-hook prompt to yes by @swati510 in #409 
 release: v0.17.0 — Distill, multi-language import resolution, light-default theme by @swati510 in #410 
 
 New Contributors 
 
 @nkgotcode made their first contribution in #376 
 
 Full Changelog : v0.16.0...v0.17.0

</details>