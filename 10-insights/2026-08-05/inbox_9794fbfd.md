---
id: inbox_9794fbfd
date: 2026-08-05
source_ref: "[[00-inbox/.../inbox_9794fbfd]]"
title: "v0.39.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.39.0
source: repowise-releases
published_at: 2026-08-05T09:58:06+00:00
fetched_at: 2026-08-06T00:23:47.475880+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "repowise v0.39.0 發布多項改進：候選檔案現展示其定義內容(而非僅路徑)，wiki 側邊欄作為綱要目錄，圖表自適應欄寬。基準測試重新評分 ContextBench(sealed half 通關後)、更新 token 效率數據、獨立報告 agent-loop 結果。修復漂移的全文索引(先前拒絕開啟)。依賴更新：aiohttp、cryptography、gitpython、postcss、undici、fast-uri。"
key_points:
  - "候選檔案定義展示：顯示檔案實現內容而非單純路徑，提升快速理解"
  - "基準改進：ContextBench 重評、token 效率指標更新、agent-loop 結果獨立化報告"
  - "索引修復：自動修復漂移的全文搜尋索引，恢復無法開啟的檔案庫"
tags: [repowise, code-analysis, benchmarks, search]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.39.0

repowise v0.39.0 發布多項改進：候選檔案現展示其定義內容(而非僅路徑)，wiki 側邊欄作為綱要目錄，圖表自適應欄寬。基準測試重新評分 ContextBench(sealed half 通關後)、更新 token 效率數據、獨立報告 agent-loop 結果。修復漂移的全文索引(先前拒絕開啟)。依賴更新：aiohttp、cryptography、gitpython、postcss、undici、fast-uri。

### 重點
- 候選檔案定義展示：顯示檔案實現內容而非單純路徑，提升快速理解
- 基準改進：ContextBench 重評、token 效率指標更新、agent-loop 結果獨立化報告
- 索引修復：自動修復漂移的全文搜尋索引，恢復無法開啟的檔案庫

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.39.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.39.0

What's Changed 
 
 feat(answer): name what each candidate file defines, not just its path by @RaghavChamadiya in #1306 
 docs(benchmarks): rescore ContextBench on the sealed half after the gate fixes by @RaghavChamadiya in #1307 
 docs(benchmarks): tighten section 1 and refresh the token-efficiency figures by @RaghavChamadiya in #1308 
 docs(benchmarks): report the agent-loop result, and separate it from the payload number by @RaghavChamadiya in #1310 
 fix(search): repair a drifted full-text index instead of refusing to open it by @RaghavChamadiya in #1311 
 feat(docs): read the wiki sidebar as a table of contents, and fit diagrams to the column by @RaghavChamadiya in #1312 
 chore(deps): bump aiohttp, cryptography, gitpython, postcss, undici, fast-uri by @RaghavChamadiya in #1313 
 release: v0.39.0 — candidate defines, a sidebar that reads as an outline, and a store that opens again by @RaghavChamadiya in #1314 
 
 Full Changelog : v0.38.0...v0.39.0

</details>