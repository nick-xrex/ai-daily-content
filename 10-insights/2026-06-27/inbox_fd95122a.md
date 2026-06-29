---
id: inbox_fd95122a
date: 2026-06-27
source_ref: "[[00-inbox/2026-06-27/2200-repowise-releases-v0-25-0-b8f6]]"
title: "v0.25.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.25.0
source: repowise-releases
published_at: 2026-06-27T13:29:22+00:00
fetched_at: 2026-06-27T22:05:09.635937+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.25.0 發布，新增 Split File 模組分解檢測與 Extract Method 重構兩大功能。Split File detector 透過 cohesion 信號與內部過程 CFG 層分析識別應拆分的模組，並在 web UI 與 code-gen 中輸出重構規劃；Extract Method 支援 def/use 與 reaching definitions 分析，已擴展至 Go、TypeScript/JavaScript 三種語言。其他改進包括：虛擬化工作空間表格與 DSM grid 提升 UI 性能、coverage 報告在索引時自動攝取、修正 decision harvest 的 title-only records、強化程式碼健康驗證與架構文檔。此版本擴充 Repowise 的自動重構工具組能力。"
key_points:
  - "Split File detector：透過 cohesion 信號與 CFG dataflow 分析識別模組分解機會，產出 web UI 與 code-gen 規劃"
  - "Extract Method 跨語言支援：Go、TypeScript/JavaScript 新增支援，基於 CFG 的 def/use 與 reaching definitions 分析"
  - "UI 與資料品質改進：虛擬化表格提升性能、coverage 自動攝取、修正 decision harvest 重複紀錄問題"
tags: [repowise, refactoring, code-generation, code-quality]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.25.0

Repowise v0.25.0 發布，新增 Split File 模組分解檢測與 Extract Method 重構兩大功能。Split File detector 透過 cohesion 信號與內部過程 CFG 層分析識別應拆分的模組，並在 web UI 與 code-gen 中輸出重構規劃；Extract Method 支援 def/use 與 reaching definitions 分析，已擴展至 Go、TypeScript/JavaScript 三種語言。其他改進包括：虛擬化工作空間表格與 DSM grid 提升 UI 性能、coverage 報告在索引時自動攝取、修正 decision harvest 的 title-only records、強化程式碼健康驗證與架構文檔。此版本擴充 Repowise 的自動重構工具組能力。

### 重點
- Split File detector：透過 cohesion 信號與 CFG dataflow 分析識別模組分解機會，產出 web UI 與 code-gen 規劃
- Extract Method 跨語言支援：Go、TypeScript/JavaScript 新增支援，基於 CFG 的 def/use 與 reaching definitions 分析
- UI 與資料品質改進：虛擬化表格提升性能、coverage 自動攝取、修正 decision harvest 重複紀錄問題

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.25.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's Changed 
 
 perf(ui): virtualize workspace tables and bound the DSM grid by @swati510 in #602 
 release: v0.24.1 by @swati510 in #603 
 feat(health): ingest coverage reports during indexing by @RaghavChamadiya in #604 
 fix(decisions): stop decision harvest emitting title-only records by @RaghavChamadiya in #605 
 feat(refactor): add Split File detector for module decomposition by @RaghavChamadiya in #607 
 feat(refactor): surface Split File plans in the web UI and code-gen by @RaghavChamadiya in #608 
 feat(health): intra-procedural CFG core for flagged functions by @RaghavChamadiya in #612 
 feat(health): def/use and reaching definitions over the CFG by @RaghavChamadiya in #613 
 feat(health): Extract Method refactoring over the dataflow layer by @RaghavChamadiya in #615 
 docs: strengthen code-health validation story and fix stale references by @RaghavChamadiya in #617 
 Port Extract Method to Go and TypeScript/JavaScript by @RaghavChamadiya in #616 
 feat(refactor): richer cohesion signals for Split File by @RaghavChamadiya in #614 
 docs(health): tighten code-health docs, name CodeScene, shift internals to architecture doc by @RaghavChamadiya in #618 
 docs(health): rename user-facing "biomarker" to "marker" (display copy only) by @RaghavChamadiya in #619 
 fix: handle '.' as glob pattern on Python 3.14+ by @madmansn0w in #609 
 release: v0.25.0 - Split File + Extract Method refactoring, coverage ingestion by @RaghavChamadiya in #620 
 
 New Contributors 
 
 @madmansn0w made their first contribution in #609 
 
 Full Changelog : v0.24.0...v0.25.0

</details>