---
id: inbox_52ecfaf8
date: 2026-07-08
source_ref: "[[00-inbox/.../inbox_52ecfaf8]]"
title: "v0.28.1"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.28.1
source: repowise-releases
published_at: 2026-07-08T07:56:35+00:00
fetched_at: 2026-07-10T00:46:26.759992+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.28.1 發布，主要改進性能指標與可視化體驗。修正了性能覆蓋率的死標記處理（dead perf markers），引入性能地圖著色改進（按發現和覆蓋率著色而非評分），改善了 UI 決策守衛和標籤，提升了圖表可視性和狀態說明清晰度。"
key_points:
  - "Dead performance markers correctly wired; coverage honesty fixes in health metrics"
  - "Performance map colored by findings/coverage metrics (not score) for better insight"
  - "UI improvements: decisions guards, enforcement prompts, health drawer polish"
tags: [repowise, performance-analysis, ui-ux]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.28.1

Repowise v0.28.1 發布，主要改進性能指標與可視化體驗。修正了性能覆蓋率的死標記處理（dead perf markers），引入性能地圖著色改進（按發現和覆蓋率著色而非評分），改善了 UI 決策守衛和標籤，提升了圖表可視性和狀態說明清晰度。

### 重點
- Dead performance markers correctly wired; coverage honesty fixes in health metrics
- Performance map colored by findings/coverage metrics (not score) for better insight
- UI improvements: decisions guards, enforcement prompts, health drawer polish

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.28.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.28.1

What's Changed 
 
 fix(health): wire dead perf markers and surface honest performance coverage by @RaghavChamadiya in #711 
 feat(health): interprocedural quadratic-loop taint primitive (validated, unsurfaced) by @RaghavChamadiya in #712 
 revert: drop the unsurfaced interprocedural quadratic-loop primitive ( #712 ) by @RaghavChamadiya in #713 
 feat(health): color the performance map by findings and coverage, not the score by @RaghavChamadiya in #716 
 fix(ui): decisions guards + enforcement prompt, honest stats labels, health-drawer polish by @swati510 in #715 
 fix(graph): keep dead/hot/flow nodes visible on capped graphs; explain layout and overlay states by @swati510 in #714 
 release: v0.28.1 — graph overlay visibility, decisions/health presentation fixes by @swati510 in #717 
 
 Full Changelog : v0.28.0...v0.28.1

</details>