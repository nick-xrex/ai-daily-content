---
id: inbox_58fd38ea
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.29.0"
author: "github-actions[bot]"
published_at: 2026-07-09T09:59:13+00:00
fetched_at: 2026-07-09T22:09:37.570850+00:00
content_hash: "bfa97e32f7a6b3d0de24bb562e463b35285b1ccc881350c5d6a9702905f5762d"
lang: en
caption_quality: None
raw: true
topics: []
---

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