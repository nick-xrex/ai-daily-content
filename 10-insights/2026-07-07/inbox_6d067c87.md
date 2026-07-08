---
id: inbox_6d067c87
date: 2026-07-07
source_ref: "[[00-inbox/.../inbox_6d067c87]]"
title: "v0.28.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.28.0
source: repowise-releases
published_at: 2026-07-07T15:10:04+00:00
fetched_at: 2026-07-08T01:01:17.685097+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.28.0 發佈，著重增量更新可靠性、代碼分析精度及語言支援擴展。新增 Lean 4 語言支援（輕量級正規表達式層級）；修正代碼健康度誤判問題（改進群組化、主要原因辨識、值域下限計算）；強化知識圖譜增量重建與原子性持久化機制；新增 fetchAllPaginated 分頁輔助工具；修正 Go 語言未使用匯出偽陽性及 GitHub noreply 郵箱重複計數問題；包含端對端與可靠性測試覆蓋。"
key_points:
  - "新增 Lean 4 語言支援（輕量級正規表達式層級）"
  - "修正代碼健康度誤判：群組化、主要原因判別、值域下限"
  - "增量更新可靠性：原子性持久化、並發鎖定、完整失敗回報"
tags: [repowise, language-support, code-analysis, update-reliability]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.28.0

Repowise v0.28.0 發佈，著重增量更新可靠性、代碼分析精度及語言支援擴展。新增 Lean 4 語言支援（輕量級正規表達式層級）；修正代碼健康度誤判問題（改進群組化、主要原因辨識、值域下限計算）；強化知識圖譜增量重建與原子性持久化機制；新增 fetchAllPaginated 分頁輔助工具；修正 Go 語言未使用匯出偽陽性及 GitHub noreply 郵箱重複計數問題；包含端對端與可靠性測試覆蓋。

### 重點
- 新增 Lean 4 語言支援（輕量級正規表達式層級）
- 修正代碼健康度誤判：群組化、主要原因判別、值域下限
- 增量更新可靠性：原子性持久化、並發鎖定、完整失敗回報

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.28.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.28.0

What's Changed 
 
 ci: scope publish.yml tag filter to v[0-9]* (avoid vscode-v* collision) by @RaghavChamadiya in #663 
 fix(health): resolve code-health false-flag presentation (grouping, dominant cause, floor magnitude) by @swati510 in #700 
 feat: Add Lean 4 language support (lightweight regex tier) by @mvanhorn in #600 
 docs: publish verified no-key quickstart (README + repowise.dev) by @RaghavChamadiya in #627 
 feat(api-client): add fetchAllPaginated pagination helper by @Ayush7614 in #682 
 fix(go): rescue same-file type references from unused_export false po... by @crizah in #629 
 fix(contributors): fold GitHub noreply emails so one person isn't two contributors by @swati510 in #701 
 fix(update): rebuild the knowledge graph on incremental updates by @RaghavChamadiya in #702 
 refactor(update): reconcile the workspace and single-repo update paths by @RaghavChamadiya in #703 
 fix(update): atomic persistence, atomic locking, and honest failure reporting by @RaghavChamadiya in #706 
 test(update): end-to-end and reliability coverage for repowise update by @RaghavChamadiya in #707 
 release: v0.28.0 — reliable incremental updates, Lean 4 support by @RaghavChamadiya in #709 
 
 New Contributors 
 
 @mvanhorn made their first contribution in #600 
 @crizah made their first contribution in #629 
 
 Full Changelog : v0.27.0...v0.28.0

</details>