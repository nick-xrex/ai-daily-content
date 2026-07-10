---
id: inbox_58fd38ea
date: 2026-07-09
source_ref: "[[00-inbox/.../inbox_58fd38ea]]"
title: "v0.29.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.29.0
source: repowise-releases
published_at: 2026-07-09T09:59:13+00:00
fetched_at: 2026-07-10T00:46:26.759090+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.29.0 發布，包含代碼健康檢測器的大規模準確性改進與架構重構。核心修正包括複雜度指標重新計算（elif nesting、參數、推導式、NLOC 計數方式調整）、針對閉包/作用域/worker pool 場景的假陽性削減，以及引入 NLOC-weighting 和 per-file leverage 指標提升評分精度。同時改善了 MCP payload 品質與隱私保護（contributor-email 脫敏），並重構了 CLI 和 server 代碼結構將命令和路由拆分為獨立包，擴展了代理溯源檢測管道。"
key_points:
  - "Complexity metrics recalculated: elif nesting, params, comprehensions, NLOC for improved accuracy"
  - "False positive reduction targeting closures, scopes, worker pools via specialized analysis"
  - "New metrics: NLOC-weighting, per-file leverage; MCP payload quality enhanced; contributor-email privacy protection"
tags: [repowise, code-health, static-analysis, metrics]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.29.0

Repowise v0.29.0 發布，包含代碼健康檢測器的大規模準確性改進與架構重構。核心修正包括複雜度指標重新計算（elif nesting、參數、推導式、NLOC 計數方式調整）、針對閉包/作用域/worker pool 場景的假陽性削減，以及引入 NLOC-weighting 和 per-file leverage 指標提升評分精度。同時改善了 MCP payload 品質與隱私保護（contributor-email 脫敏），並重構了 CLI 和 server 代碼結構將命令和路由拆分為獨立包，擴展了代理溯源檢測管道。

### 重點
- Complexity metrics recalculated: elif nesting, params, comprehensions, NLOC for improved accuracy
- False positive reduction targeting closures, scopes, worker pools via specialized analysis
- New metrics: NLOC-weighting, per-file leverage; MCP payload quality enhanced; contributor-email privacy protection

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.29.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.29.0

What's Changed 
 
 fix(upgrade): resync bundled changelog with docs for v0.28.1 by @swati510 in #718 
 feat(health): surface NLOC-weighting and per-file leverage in get_health by @RaghavChamadiya in #719 
 fix(update-lock): make lock creation atomic to stop double-acquire by @swati510 in #720 
 refactor(cli): split health_cmd into a command package by @RaghavChamadiya in #721 
 refactor(cli): split augment_cmd into a package by @RaghavChamadiya in #722 
 refactor(cli): split doctor_cmd into a package by @RaghavChamadiya in #723 
 refactor(server): split code_health router into a package by @RaghavChamadiya in #724 
 refactor(server): split tool_risk into a package by @RaghavChamadiya in #725 
 refactor(core): split crud/analysis into per-entity modules by @RaghavChamadiya in #726 
 feat(server): compact get_overview payload by default by @RaghavChamadiya in #729 
 feat(git): extend agent-provenance detection channels by @RaghavChamadiya in #731 
 test(server): align get_overview module-cap test with cap=8 by @RaghavChamadiya in #732 
 fix(mcp): payload quality and contributor-email privacy by @swati510 in #737 
 fix(health): correct god-class, SQL LIMIT, large-method, and coupling findings by @swati510 in #736 
 fix(health): cut false performance flags around closures, scope, and worker pools by @swati510 in #735 
 fix(health): correct complexity-metric miscounts (elif nesting, params, comprehensions, NLOC) by @swati510 in #734 
 fix(health): give error-handling findings honest rationales by @swati510 in #733 
 release: v0.29.0 — code-health detector honesty + MCP payload/privacy by @swati510 in #738 
 
 Full Changelog : v0.28.1...v0.29.0

</details>