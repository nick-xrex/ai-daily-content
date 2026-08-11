---
id: inbox_231f9172
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.40.0"
author: "github-actions[bot]"
published_at: 2026-08-10T14:37:27+00:00
fetched_at: 2026-08-10T22:07:45.415544+00:00
content_hash: "57b0b666fe617dce6371679bf53b93f4e3677266147b767e73f1d9a61dbfd2a2"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.40.0

What's Changed 
 
 docs(vscode): release notes for the 0.7.0 extension release by @RaghavChamadiya in #1304 
 fix(decisions): ground each marker decision in its own span, and stop scoring untouched files as stale by @RaghavChamadiya in #1315 
 refactor(sessions): make the transcript layer harness-agnostic by @RaghavChamadiya in #1316 
 feat(precedent): record structural facts about a checkout at index time by @RaghavChamadiya in #1317 
 feat(answer): surface a recorded fact that disagrees with an answer by @RaghavChamadiya in #1318 
 docs(benchmarks): rerun section 2 on a second agent harness, and correct the adoption claim by @RaghavChamadiya in #1319 
 docs(benchmarks): lead with the 48-question Codex run, and describe the retrieval fix as a fix by @RaghavChamadiya in #1321 
 feat(decisions): bind a record to the directories it governs, and measure staleness by @RaghavChamadiya in #1322 
 feat(episodes): Record each code fix as a dated change bound to the files it touched by @RaghavChamadiya in #1324 
 feat(episodes): record each agent session as a local, dated episode bound to the files it touched by @RaghavChamadiya in #1325 
 feat(episodes): keep a session after its transcript is pruned, and search episode bodies by @RaghavChamadiya in #1331 
 feat(episodes): answer "what happened here" from get_why, and count it on the risk and context cards by @RaghavChamadiya in #1333 
 fix(mcp): bring the get_risk docstring back under the schema budget by @RaghavChamadiya in #1334 
 fix(hooks): stop counting an injection nothing could disagree with as followed by @RaghavChamadiya in #1335 
 feat(hooks): answer a failed path with the file the index says you meant by @RaghavChamadiya in #1336 
 fix(health): stop get_health returning 4.7MB, and index the table it reads by @RaghavChamadiya in #1337 
 docs: correct code-health marker taxonomy and stale benchmark claims by @RaghavChamadiya in #1338 
 Retire the skeleton-nudge Read hook by @RaghavChamadiya in #1339 
 docs(benchmarks): discharge the Opus promise, name RTK, state the code-only scope by @RaghavChamadiya in #1340 
 fix(codex): Match the Codex shell tool by the names Codex actually sends by @RaghavChamadiya in #1341 
 fix(health): rank the worst-files lists by deduction, not by a score that clamps at 1.0 by @RaghavChamadiya in #1342 
 fix(cli): report what a surface is actually doing, not what it once did by @RaghavChamadiya in #1343 
 fix(health): show the line on file-level findings, and stop one biomarker flooding the drawer by @RaghavChamadiya in #1344 
 perf(health): stop shipping every file's findings in the refactoring-targets list by @RaghavChamadiya in #1345 
 feat(episodes): serve recorded episodes over HTTP by @RaghavChamadiya in #1346 
 perf(health): stop the overview route reading both health tables twice by @RaghavChamadiya in #1350 
 perf(health): stop the badge reading the whole dataset, and index symbols by file by @RaghavChamadiya in #1351 
 feat(decisions): say what the page actually knows by @RaghavChamadiya in #1352 
 fix(graph): stop reporting a Go package as a circular dependency by @RaghavChamadiya in #1354 
 fix(core/cli): do not cache failed update-check results by @Ayush7614 in #1330 
 fix(tests): give the SCC test double the state the mixin reads by @RaghavChamadiya in #1355 
 feat(sessions): add Codex session transcript adapter support by @rehan6025 in #1277 
 perf(health): stop two dashboard routes reading tables they barely use by @RaghavChamadiya in #1356 
 fix(health): stop the directive promising a fix it does not have by @RaghavChamadiya in #1358 
 fix(health): make module the package boundary, not a graph community label by @RaghavChamadiya in #1359 
 fix(update): stop a config change advancing the sync pointer past commits it never indexed by @RaghavChamadiya in #1360 
 fix(health): stop only dropping the totals, and bucket test files out of the headline findings by @RaghavChamadiya in #1361 
 feat(hooks): collapse unchanged re-reads, and report what the hooks cost by @RaghavChamadiya in #1362 
 fix(watch): index the working tree, so 
epowise watch actually updates by @RaghavChamadiya in #1363 
 fix(health): let a file at the score floor show movement, and stop the trend hiding improvements by @RaghavChamadiya in #1364 
 docs: put the numbers where people actually look by @RaghavChamadiya in #1365 
 fix(health): give Go, Maven and Ruby monorepos real module attribution, without a re-index by @RaghavChamadiya in #1366 
 feat: verify returned vector width across all embedding providers by @akshatmalik-bruh in #1305 
 fix(cli): correct _read_output_line_count for trailing newlines by @Ayush7614 in #1328 
 fix(core): pass unbounded limit to list_jobs from resume readers by @Ayush7614 in #1329 
 fix(status/doctor): query configured DB when no local wiki.db exists by @Ameysr in #1320 
 feat(claude-plugin): add /repowise:security slash command by @Ayush7614 in #1107 
 docs(website): sync CLI and Claude plugin pages with shipped surface by @Ayush7614 in #1106 
 docs(examples): add change-risk CLI walkthrough by @Ayush7614 in #1177 
 fix(refactoring): stop three plan fields from reporting constants as measurements by @RaghavChamadiya in #1374 
 fix(tests): make the integration JobStore double honour its filters by @RaghavChamadiya in #1375 
 perf(update): stop four repeated costs in the update prologue by @RaghavChamadiya in #1376 
 fix(update): prune deleted files, and stop a degraded run stranding its range by @RaghavChamadiya in #1377 
 fix(search): stop ranking on a keyless index's own vectors by @RaghavChamadiya in #1378 
 perf(update): fold lifetime churn onto an anchor instead of re-walking history by @RaghavChamadiya in #1379 
 fix(keyless): close two unguarded vector reads and the confidence hole by @RaghavChamadiya in #1380 
 perf(update): stop rewriting the graph rows an update did not change by @RaghavChamadiya in #1381 
 perf(agent): slim the resident CLAUDE.md block and stop waking hooks on shell commands by @RaghavChamadiya in #1382 
 fix(generation): stop a keyless wiki warning about every page it has by @RaghavChamadiya in #1383 
 fix(dead-code): persist the repo-wide verdict an update already computed by @RaghavChamadiya in #1389 
 fix: unwedge get_why, and four defects found smoke-testing the release by @RaghavChamadiya in #1395 
 fix(server): serve only indexed files from /file-content by @RaghavChamadiya in #1397 
 fix(server): decide keyless access from the peer address, not REPOWISE_HOST by @RaghavChamadiya in #1401 
 release: v0.40.0 - two server security fixes, episodes, and a much cheaper update by @RaghavChamadiya in #1396 
 
 New Contributors 
 
 @rehan6025 made their first contribution in #1277 
 @Ameysr made their first contribution in #1320 
 
 Full Changelog : v0.39.0...v0.40.0