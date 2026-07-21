---
id: inbox_5a2e45a1
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.34.0"
author: "github-actions[bot]"
published_at: 2026-07-20T09:45:07+00:00
fetched_at: 2026-07-20T22:50:29.646321+00:00
content_hash: "3c5bb354ecaf5db0a64866915966e24834c0ad28d9ea5affca788d25d2a4843a"
lang: en
caption_quality: None
raw: true
topics: []
---

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