---
id: inbox_8183bdea
date: 2026-06-25
source_ref: "[[00-inbox/2026-06-25/2200-repowise-releases-v0-24-0-d897]]"
title: "v0.24.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.24.0
source: repowise-releases
published_at: 2026-06-25T11:22:05+00:00
fetched_at: 2026-06-25T22:06:10.295748+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.24.0 推出「重構智能」版本。新增四種確定性重構檢測器（Extract Class、Extract Helper、Move Method、Break Cycle），無須 LLM 依賴即可建議重構。引入 opt-in LLM 代碼生成功能，可從確定性計畫自動生成代碼並提供 diff 檢視。新建 Web Refactoring 分頁整合排序計畫卡與 agent 匯出；Code Health 概觀新增 Findings 工作台；Files 頁面改版為可瀏覽清單與深色模式支持；虛擬化大表格以提升性能。"
key_points:
  - "四種確定性重構檢測器（Extract Class、Extract Helper、Move Method、Break Cycle）與 LLM 代碼生成分離，降低依賴風險"
  - "opt-in LLM 代碼生成從確定性計畫產出代碼，搭配 diff 檢視，用戶可視化驗證"
  - "Web Refactoring 分頁整合排序計畫卡和 agent 匯出，Code Health 工作台集中展示檢測發現"
tags: [refactoring-intelligence, code-generation, deterministic-detection, code-health]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.24.0

Repowise v0.24.0 推出「重構智能」版本。新增四種確定性重構檢測器（Extract Class、Extract Helper、Move Method、Break Cycle），無須 LLM 依賴即可建議重構。引入 opt-in LLM 代碼生成功能，可從確定性計畫自動生成代碼並提供 diff 檢視。新建 Web Refactoring 分頁整合排序計畫卡與 agent 匯出；Code Health 概觀新增 Findings 工作台；Files 頁面改版為可瀏覽清單與深色模式支持；虛擬化大表格以提升性能。

### 重點
- 四種確定性重構檢測器（Extract Class、Extract Helper、Move Method、Break Cycle）與 LLM 代碼生成分離，降低依賴風險
- opt-in LLM 代碼生成從確定性計畫產出代碼，搭配 diff 檢視，用戶可視化驗證
- Web Refactoring 分頁整合排序計畫卡和 agent 匯出，Code Health 工作台集中展示檢測發現

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.24.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's Changed 
 
 fix(graph): stop execution-flow entry-point scores from being wiped on update by @RaghavChamadiya in #585 
 feat(health): deterministic Extract Class refactoring suggestions by @RaghavChamadiya in #586 
 feat(health): deterministic Extract Helper refactoring detector by @RaghavChamadiya in #587 
 feat(health): add Move Method and Break Cycle refactoring detectors by @RaghavChamadiya in #588 
 feat(health): web Refactoring tab with ranked plan cards and agent export by @RaghavChamadiya in #589 
 feat(refactoring): file-first cards, browsable list, and a visual plan modal by @RaghavChamadiya in #590 
 feat(files): browsable Files page, table restyle, dark-mode polish by @RaghavChamadiya in #591 
 feat(refactoring): opt-in LLM code generation from deterministic plans by @RaghavChamadiya in #592 
 feat(health): airy Code Health overview with a Findings workbench by @RaghavChamadiya in #593 
 feat(refactoring): generate code from plans with a diff viewer by @RaghavChamadiya in #594 
 docs: lead with the code-health loop and document refactoring intelligence by @RaghavChamadiya in #595 
 test(ui): fix stale Code Health lens-switch test by @RaghavChamadiya in #596 
 perf(ui): virtualize large tables with a shared windowing primitive by @swati510 in #598 
 feat(init): docs toggle in Advanced, configurable index-only, raise commit cap by @RaghavChamadiya in #599 
 release: v0.24.0 — refactoring intelligence by @RaghavChamadiya in #601 
 
 Full Changelog : v0.23.0...v0.24.0

</details>