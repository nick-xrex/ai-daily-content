---
id: inbox_13b0568f
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.22.0"
author: "github-actions[bot]"
published_at: 2026-06-22T14:49:59+00:00
fetched_at: 2026-06-25T22:00:26.048283+00:00
content_hash: "e7abd56659848d013a32d6943c84d1a962fce553d54566d393fd72a903692e28"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.22.0

What's Changed 
 
 fix(freshness): keep CLAUDE.md stamp and indexed commit current by @RaghavChamadiya in #524 
 refactor(ingestion): flatten deep nesting in heritage extractors by @RaghavChamadiya in #526 
 Split code-health score into defect, maintainability, and performance dimensions by @RaghavChamadiya in #528 
 feat(external-systems): classify dependencies by I/O boundary kind by @RaghavChamadiya in #529 
 refactor(mcp): decompose high-complexity MCP tool handlers by @RaghavChamadiya in #527 
 feat(health): add io-in-loop performance detector by @RaghavChamadiya in #530 
 feat(health): surface maintainability as a second health signal by @RaghavChamadiya in #531 
 feat(health): cross-function io-in-loop / N+1 detection by @RaghavChamadiya in #532 
 feat(health): surface performance as a co-equal third health signal by @RaghavChamadiya in #533 
 docs(readme): surface three-signal code health + star CTAs by @RaghavChamadiya in #534 
 docs(banner): add a subtle star CTA to the header image by @RaghavChamadiya in #535 
 refactor(health): extract perf detection into a PerfDialect plugin registry by @RaghavChamadiya in #536 
 feat(health): add Java, Go, and C# performance dialects by @RaghavChamadiya in #537 
 Add loop-level performance markers across language dialects by @RaghavChamadiya in #538 
 feat(health): centrality-gated performance markers + reusable severity ranker by @RaghavChamadiya in #539 
 fix(health): eliminate three perf-detector false-positive classes (C#/Go/Python) by @RaghavChamadiya in #540 
 feat(health): language-specific perf markers + precision refinements by @RaghavChamadiya in #541 
 feat(health): add pandas_iterrows_in_loop performance marker by @RaghavChamadiya in #542 
 feat(health): surface performance as a co-equal pillar in the web UI by @RaghavChamadiya in #544 
 fix(health): skip for...of over constant collections in TS/JS perf detector by @RaghavChamadiya in #545 
 feat(health): MCP-native AI prompt flavor + finding-count cap by @RaghavChamadiya in #546 
 feat(health): roll AI prompt actions across the dashboard by @RaghavChamadiya in #547 
 feat(web): repo Stats "By the Numbers" page by @RaghavChamadiya in #548 
 feat: aggregate cross-repo co-changes by repo pair with drill-down (Resolves #482 ) by @d3vpool in #543 
 feat(commits): Code Evolution timeline as the headline by @RaghavChamadiya in #549 
 feat(impact): redesign the blast-radius impact tab by @RaghavChamadiya in #550 
 feat(owners): lead with a knowledge-distribution headline by @RaghavChamadiya in #551 
 fix(commits): commits-page follow-ups (full-width agent strip, collapsible risk panel, repo-wide stat cards) by @RaghavChamadiya in #552 
 feat(upgrade): store-format versioning for reindex-free upgrades by @RaghavChamadiya in #553 
 feat(cli): release advisory and "what's new" for upgrades by @RaghavChamadiya in #554 
 feat(web): surface upgrades in the dashboard by @RaghavChamadiya in #556 
 feat(cli): central platform layer + anonymous opt-out telemetry by @RaghavChamadiya in #555 
 refactor(health): split complexity walker into focused modules by @RaghavChamadiya in #557 
 feat(mcp): hybrid symbol and path search in search_codebase ( #484 ) by @RaghavChamadiya in #558 
 feat(distill): seamless rewrite permissions + re-read savings by @RaghavChamadiya in #559 
 fix(dead-code): rescue Python symbols used only within their own file by @RaghavChamadiya in #563 
 README release refresh: banner, numbers-first lead, combined demo GIF by @swati510 in #562 
 Hosted ⇄ Web UI parity by @swati510 in #561 
 fix(web): reflect CLI auto-syncs in overview "Last synced" by @RaghavChamadiya in #564 
 README: drop the redundant prose tagline (already in the banner) by @swati510 in #565 
 release: v0.22.0 — three-signal code health, reindex-free upgrades, hybrid search by @RaghavChamadiya in #566 
 
 New Contributors 
 
 @d3vpool made their first contribution in #543 
 
 Full Changelog : v0.21.0...v0.22.0