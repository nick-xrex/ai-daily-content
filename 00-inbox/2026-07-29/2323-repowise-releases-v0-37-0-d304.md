---
id: inbox_7a78a7aa
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.37.0"
author: "github-actions[bot]"
published_at: 2026-07-29T12:44:53+00:00
fetched_at: 2026-07-29T23:23:59.855627+00:00
content_hash: "d30431220705ea06168c63ecb986e86657883d033e3a1ed9cd3313b53301bc62"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.37.0

What's Changed 
 
 feat(init): add --no-editor-setup to skip global MCP/hook registration by @RaghavChamadiya in #1086 
 Scope the Stats page to what no other page shows by @RaghavChamadiya in #1091 
 feat(stats): rework the coding-rhythm chart and name how a repo ships by @RaghavChamadiya in #1096 
 fix(coupling): keep ?focus= in sync with the pinned file by @Real5K in #1088 
 fix(resume): keep the pages a resumed run deliberately skipped by @RaghavChamadiya in #1097 
 fix(ui): use stored concept tree for pages parented to repo root ( #1081 ) by @akshatmalik-bruh in #1085 
 docs(examples): add health-coverage walkthrough by @Ayush7614 in #1020 
 docs(examples): add OpenCode provider setup example by @Ayush7614 in #1021 
 fix(generation): enforce documentation completion by @austintraver in #1011 
 fix(generation): filter file dependency context by @austintraver in #1010 
 ci: run types and ui tests on every PR by @RaghavChamadiya in #1101 
 fix(dead-code): align default min_confidence floor to RISK_CAP_CONFIDENCE ( #1084 ) by @akshatmalik-bruh in #1087 
 fix(server): fail job explicitly on unknown execution mode ( #881 ) by @akshatmalik-bruh in #911 
 fix(generation): keep a page whose provider call failed (Refs #1089 ) by @RaghavChamadiya in #1104 
 fix(cli): surface page generation failures and resume hint on init completion ( #1094 ) by @akshatmalik-bruh in #1098 
 docs: onboard contributors through repowise itself, trim README badges by @RaghavChamadiya in #1110 
 fix(health): classify .mts/.cts tests in coverage_gradient and move_method by @RaghavChamadiya in #1111 
 refactor(core): one home for "is this path a test?" by @RaghavChamadiya in #1112 
 Convert the last test-path copies in the server to the shared rules by @RaghavChamadiya in #1113 
 feat(web): rebuild the Overview page around sections instead of cards by @RaghavChamadiya in #1114 
 Convert the last two inline test-path checks, and close the fixture gap (Refs #1103 ) by @RaghavChamadiya in #1115 
 Rebuild the docs page on the Overview's design language by @RaghavChamadiya in #1118 
 feat: load the docs page without every page's body by @RaghavChamadiya in #1120 
 feat(ui): rebuild Commits and Contributors on the section design language by @RaghavChamadiya in #1121 
 docs(examples): add security-scan walkthrough by @Ayush7614 in #1109 
 docs(commercial): acknowledge OSS full-history secret scan by @Ayush7614 in #1105 
 fix(mcp): budget get_answer synthesis per provider, not at a flat 30s by @RaghavChamadiya in #1124 
 feat(ui): rebuild the contributor profile and commit detail on the section design language by @RaghavChamadiya in #1125 
 fix(mcp): report an empty completion instead of shipping a blank answer by @RaghavChamadiya in #1126 
 feat(ui): rebuild Code Health on the section design language by @RaghavChamadiya in #1129 
 fix(ingestion): tolerate malformed .gitignore patterns by @ShotaNagafuchi in #1095 
 fix(dead-code): use dict.get() for git metadata in zombie package detector by @akshatmalik-bruh in #1128 
 feat(ui): rebuild Coverage and Dead code on the section design language by @RaghavChamadiya in #1132 
 test(cli): cover repowise security scan stub and history wiring by @Ayush7614 in #1108 
 feat(ui): rebuild Chat, Settings and Decisions on the section design language by @RaghavChamadiya in #1134 
 fix(providers): refresh stale model defaults and fix cost and temperature handling by @RaghavChamadiya in #1137 
 feat(init): first-run UX pass over the interactive init flow by @RaghavChamadiya in #1139 
 perf(cli): defer the pipeline import out of the generate engine by @RaghavChamadiya in #1140 
 fix(hooks): make the augment hook silent when its console script is missing by @RaghavChamadiya in #1141 
 fix(mcp): stop get_health dropping targets and repeating itself by @RaghavChamadiya in #1142 
 docs(examples): add distill / expand / saved walkthrough by @Ayush7614 in #1123 
 Typed node ids, and a Structurizr DSL export built on them by @swati510 in #1143 
 test(cli): cover repowise decision list/show/confirm/dismiss/health by @Ayush7614 in #1138 
 docs: remove obsolete Anthropic Message Batches / --no-batch by @Ayush7614 in #1136 
 docs(website): sync language list with 16 AST languages by @Ayush7614 in #1135 
 docs(website): sync MCP pages with the live default tool surface by @Ayush7614 in #1122 
 fix(structurizr): make the exported DSL openable, and correct three parser bugs by @RaghavChamadiya in #1144 
 feat(knowledge-graph): name what the arrows and dots mean, and rebuild the detail panel by @RaghavChamadiya in #1145 
 fix(architecture): stop the graph blaming the backend mid-load, and quiet its chrome by @RaghavChamadiya in #1146 
 fix(zoom): repair the node fixture that is failing type-check on main by @RaghavChamadiya in #1147 
 perf(architecture-graph): stop the canvas doing per-node and per-frame work, and fix what dimming blends toward by @RaghavChamadiya in #1149 
 refactor(architecture): give the graph one scope control, and stop it spending 8 seconds arriving by @RaghavChamadiya in #1150 
 feat(refactoring): lead with what the pile actually is, and plot the plans whose axes spread by @RaghavChamadiya in #1151 
 feat(files): let the map lead, and give it a key it cannot drift from by @RaghavChamadiya in #1152 
 fix(dead-code): remove duplicate operator* in C++ contract-method set (B033) by @akshatmalik-bruh in #1153 
 fix(server): un-shadow hidden test in test_mcp_workspace (F811) by @akshatmalik-bruh in #1154 
 fix(server): hold strong references to fire-and-forget asyncio tasks (RUF006) by @akshatmalik-bruh in #1155 
 fix(docs): one breadcrumb, correct reader height, wrapping backlinks by @swati510 in #1156 
 fix(search): one command palette answers a keypress by @swati510 in #1157 
 fix(nav): links land where their label says by @swati510 in #1158 
 chore(ruff): clear 508 lint violations and gate Python lint in CI by @RaghavChamadiya in #1161 
 release: v0.37.0 — the UI release by @RaghavChamadiya in #1162 
 
 New Contributors 
 
 @ShotaNagafuchi made their first contribution in #1095 
 
 Full Changelog : v0.36.0...v0.37.0