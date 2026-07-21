---
id: inbox_5a2e45a1
date: 2026-07-20
source_ref: "[[00-inbox/.../inbox_5a2e45a1]]"
title: "v0.34.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.34.0
source: repowise-releases
published_at: 2026-07-20T09:45:07+00:00
fetched_at: 2026-07-21T01:07:55.280190+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.34.0 發布，聚焦程式碼缺陷追蹤、知識圖譜視覺化、文件自動化與成本追蹤。新增「缺陷歷史」功能在各層級可見（按檔案、符號、提交；追蹤至引入 bug 的提交）；UI 標記「缺陷磁鐵」（頻繁修復的檔案/符號）供目標化重構。可縮放知識圖譜新增每節點程式碼健康度，文件簡報模式提供投影片及導引式對談，架構圖確定性生成。成本追蹤按操作標記支出、本機執行記錄為 $0、ROI 計算；信心度由回應接地質量（源材品質）校準而非檢索形狀。知識圖譜生成與頁面生成重疊以提升效能；文件於工作區更新時按倉庫重新生成。MCP get_risk/get_change_risk 現在回傳缺陷修復計數歷史；health 僅計算影響生產程式碼的 bug fixes。"
key_points:
  - "缺陷歷史全面落地：按檔案/符號/提交屬性化；追蹤至引入 bug 的提交；「缺陷磁鐵」標記高頻修復的符號 → 目標化重構"
  - "知識圖譜可縮放化 + per-node 程式碼健康度；簡報模式（投影片 + 導引式對談）+ 確定性架構圖自動生成；成本按操作標記、本機 run $0、ROI 可見"
  - "信心度由回應接地品質（源材質量）校準，非檢索形狀（數量/多樣性）→ 降低虛假信心；檢索-圖譜速度最佳化（知識圖譜生成與頁面平行化）"
tags: [repowise, bug-fix-history, knowledge-graph, code-health, cost-tracking]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.34.0

Repowise v0.34.0 發布，聚焦程式碼缺陷追蹤、知識圖譜視覺化、文件自動化與成本追蹤。新增「缺陷歷史」功能在各層級可見（按檔案、符號、提交；追蹤至引入 bug 的提交）；UI 標記「缺陷磁鐵」（頻繁修復的檔案/符號）供目標化重構。可縮放知識圖譜新增每節點程式碼健康度，文件簡報模式提供投影片及導引式對談，架構圖確定性生成。成本追蹤按操作標記支出、本機執行記錄為 $0、ROI 計算；信心度由回應接地質量（源材品質）校準而非檢索形狀。知識圖譜生成與頁面生成重疊以提升效能；文件於工作區更新時按倉庫重新生成。MCP get_risk/get_change_risk 現在回傳缺陷修復計數歷史；health 僅計算影響生產程式碼的 bug fixes。

### 重點
- 缺陷歷史全面落地：按檔案/符號/提交屬性化；追蹤至引入 bug 的提交；「缺陷磁鐵」標記高頻修復的符號 → 目標化重構
- 知識圖譜可縮放化 + per-node 程式碼健康度；簡報模式（投影片 + 導引式對談）+ 確定性架構圖自動生成；成本按操作標記、本機 run $0、ROI 可見
- 信心度由回應接地品質（源材質量）校準，非檢索形狀（數量/多樣性）→ 降低虛假信心；檢索-圖譜速度最佳化（知識圖譜生成與頁面平行化）

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.34.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.34.0

What's Changed 
 
 release(vscode): v0.4.0 — ship the accumulated bundled UI by @RaghavChamadiya in #910 
 perf(generation): overlap knowledge-graph enrichment with page generation by @RaghavChamadiya in #912 
 perf(decisions): reuse ingestion's source_map for the inline-marker scan by @RaghavChamadiya in #913 
 feat(docs): Present mode (slide deck + guided walkthrough) by @RaghavChamadiya in #914 
 feat(docs): deterministic architecture diagrams in wiki pages + present mode by @RaghavChamadiya in #915 
 feat(update): regenerate docs per repo on workspace update by @RaghavChamadiya in #916 
 feat(update): onboard a provider when a docs update needs one by @RaghavChamadiya in #917 
 feat: zoom-map Knowledge Graph with per-node code health by @RaghavChamadiya in #918 
 feat(answer): always synthesize; grade confidence post-synthesis by @swati510 in #919 
 feat(web): sharpen feedback CTA, drop recalibration banner by @RaghavChamadiya in #920 
 feat(update): refresh external systems (C4 L1) on manifest change by @RaghavChamadiya in #921 
 feat(costs): label spend by operation, record local runs at $0, surface ROI by @RaghavChamadiya in #925 
 feat(costs): count the agent savings the ledger was dropping by @RaghavChamadiya in #927 
 fix(stats): let the headline figures breathe and stop assuming Sat/Sun by @swati510 in #926 
 feat(answer): calibrate confidence on answer grounding, not retrieval shape by @swati510 in #923 
 fix(update): count onboarding pages in the generation progress total by @RaghavChamadiya in #928 
 feat(cli): make init/update quiet by default, show debug logs under --verbose by @RaghavChamadiya in #929 
 feat(health): count only bug fixes that change production code by @RaghavChamadiya in #931 
 feat(health): trace bug fixes to the commits that introduced them by @RaghavChamadiya in #939 
 feat(answer): lean high-confidence payload behind REPOWISE_ANSWER_LEAN_HIGH by @swati510 in #938 
 feat(health): attribute bug fixes to symbols and flag bug magnets by @RaghavChamadiya in #940 
 feat(cli): add verbose logging to restyle by @lntutor in #936 
 feat(cli): add verbose logging to claude-md by @lntutor in #937 
 feat(cli): add verbose logging to coverage add by @lntutor in #942 
 feat(cli): add verbose logging to health by @lntutor in #943 
 feat(cli): add verbose logging to workspace by @lntutor in #944 
 feat(cli): add verbose logging to watch by @lntutor in #941 
 feat(mcp): surface counted bug-fix history on get_risk and get_change_risk by @RaghavChamadiya in #946 
 feat(cli): warn at edit time when a file has a run of recent bug fixes by @RaghavChamadiya in #947 
 feat(health): show per-file bug-fix history in the drawer, panel and hover by @RaghavChamadiya in #948 
 feat(symbols): show and filter by per-symbol bug-fix counts by @RaghavChamadiya in #949 
 feat(commits): replace the file-risk bars with commit-level distribution views by @RaghavChamadiya in #950 
 chore(git-indexer): drop the SZZ blame pass by @RaghavChamadiya in #951 
 fix(commits): count author experience over the whole history, not the update batch by @RaghavChamadiya in #953 
 fix(claude-md): rank the generated attention list by bug-fix history, not churn by @RaghavChamadiya in #954 
 fix(mcp): make the docstring budget test environment-independent, trim get_change_risk by @RaghavChamadiya in #955 
 fix(mcp): rank get_risk's attention list and get_context's triage on fix history by @RaghavChamadiya in #956 
 docs: overhaul the README and restructure the docs tree by @RaghavChamadiya in #957 
 chore(deps): bump mcp from 1.26.0 to 1.28.1 by @RaghavChamadiya in #958 
 release: v0.34.0 — bug-fix history everywhere, zoomable knowledge graph, present mode by @RaghavChamadiya in #959 
 
 New Contributors 
 
 @lntutor made their first contribution in #936 
 
 Full Changelog : v0.33.0...v0.34.0

</details>