---
id: inbox_e9716d81
date: 2026-07-16
source_ref: "[[00-inbox/.../inbox_e9716d81]]"
title: "v0.32.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.32.0
source: repowise-releases
published_at: 2026-07-16T12:18:48+00:00
fetched_at: 2026-07-17T00:47:19.358333+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.32.0 正式版本發布，標題為「全代碼庫檢索覆蓋、答案品質改進、新統計信號」。新增 Kimi 首類提供商支持、導入編碼節奏（coding-rhythm）、動量（momentum）、卡車係數（truck factor）、循環信號（cycle signals）四大項目健康度量。改進涵蓋 Anthropic thinking blocks 原生處理、MCP 聯合答案延遲至綜合階段、測試檔破壞性獨立追蹤、Go 函數參照檢測、Dataflow 遞迴至 with 語句體。檢索品質升級透過按符號重要性排序、確定性邊界生成、向量索引持久化、Next.js 中間件代理。UI 與搜尋改進包括數字格式化、年齡顯示、信心度評分歸一化。共新增六位貢獻者。"
key_points:
  - "Truck factor、coding-rhythm、momentum、cycle signals 四大新統計度量提供項目健康動態評估，可跨專案應用"
  - "Kimi 提供商一級支持與 Anthropic thinking blocks 原生整合，擴展 LLM 相容性"
  - "全代碼庫檢索精準度提升：按符號重要性排序、Dataflow 遞迴深化、Go 死程式碼誤判修復"
tags: [repowise-v0-32, code-metrics, kimi-provider, anthropic-integration, retrieval-quality]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## v0.32.0

Repowise v0.32.0 正式版本發布，標題為「全代碼庫檢索覆蓋、答案品質改進、新統計信號」。新增 Kimi 首類提供商支持、導入編碼節奏（coding-rhythm）、動量（momentum）、卡車係數（truck factor）、循環信號（cycle signals）四大項目健康度量。改進涵蓋 Anthropic thinking blocks 原生處理、MCP 聯合答案延遲至綜合階段、測試檔破壞性獨立追蹤、Go 函數參照檢測、Dataflow 遞迴至 with 語句體。檢索品質升級透過按符號重要性排序、確定性邊界生成、向量索引持久化、Next.js 中間件代理。UI 與搜尋改進包括數字格式化、年齡顯示、信心度評分歸一化。共新增六位貢獻者。

### 重點
- Truck factor、coding-rhythm、momentum、cycle signals 四大新統計度量提供項目健康動態評估，可跨專案應用
- Kimi 提供商一級支持與 Anthropic thinking blocks 原生整合，擴展 LLM 相容性
- 全代碼庫檢索精準度提升：按符號重要性排序、Dataflow 遞迴深化、Go 死程式碼誤判修復

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.32.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.32.0

What's Changed 
 
 fix(onboarding): rank Key Concepts by symbol importance and ground citations by @RaghavChamadiya in #813 
 feat(generation): deterministic coverage for the undocumented file tail by @RaghavChamadiya in #817 
 feat(docs): surface and down-rank the deterministic coverage tail by @RaghavChamadiya in #819 
 feat(telemetry): MCP tool-call events, interrupted status, index-shape outcomes by @RaghavChamadiya in #820 
 fix: handle Anthropic thinking blocks by @tomasvn20 in #787 
 feat(risk): split test-file breakage out of will_break ( #672 ) by @Real5K in #739 
 fix(mcp): defer answer-by-union to synthesis when the mention is incidental by @RaghavChamadiya in #823 
 feat: add first-class Kimi provider by @Real5K in #824 
 feat(codex): deliver architectural decisions into Codex SessionStart by @DresdenGman in #788 
 fix(stats): report true project age, commit and contributor counts ( #730 ) by @RaghavChamadiya in #827 
 feat(stats): coding-rhythm, momentum, truck factor and cycle signals by @RaghavChamadiya in #828 
 fix(ui): compact k/m number formatting and years/months age display in stats hero by @mvanhorn in #798 
 fix(server): load persisted vector indexes by @GautamSharma99 in #835 
 Fix #838 : Use Next.js Middleware for dynamic proxying of API routes by @kishansaaai in #839 
 fix(chat): show normalized confidence in source citations, not raw score by @RaghavChamadiya in #846 
 fix(go): detect function references in go to rescue FPs on dead-code by @crizah in #815 
 fix(dataflow): recurse into with-statement bodies by @Real5K in #836 
 fix(ui): make empty doc state friendlier by @Real5K in #822 
 fix(web): contain overflowing modal inputs in Add Repository dialog ( #843 ) by @jyotirmya17 in #844 
 fix(search): score symbols on the query's identifier, not the whole question by @swati510 in #853 
 release: v0.32.0 — full-codebase retrieval coverage, answer-quality fixes, new stats signals by @swati510 in #854 
 
 New Contributors 
 
 @tomasvn20 made their first contribution in #787 
 @Real5K made their first contribution in #739 
 @DresdenGman made their first contribution in #788 
 @GautamSharma99 made their first contribution in #835 
 @kishansaaai made their first contribution in #839 
 @jyotirmya17 made their first contribution in #844 
 
 Full Changelog : v0.31.0...v0.32.0

</details>