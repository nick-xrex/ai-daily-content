---
id: inbox_3fdc834b
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.31.0"
author: "github-actions[bot]"
published_at: 2026-07-12T11:52:12+00:00
fetched_at: 2026-07-12T22:23:55.362854+00:00
content_hash: "74a48cf07b75c4878c3b2344bcaa14dbe8f5bcb161f1bad0225ae7442ede0c49"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.31.0

What's Changed 
 
 test(vscode): fix flaky home-sidebar summary-failure assertion by @swati510 in #766 
 feat(mcp): session-survival hardening for the tool surface by @RaghavChamadiya in #767 
 feat(languages): parse shell to AST (functions, source edges, complexity) by @RaghavChamadiya in #768 
 fix(mcp): keep non-path node ids out of get_answer fallback_targets by @RaghavChamadiya in #769 
 fix(mcp): honesty signals for zero-exact search and filename-only get_symbol by @RaghavChamadiya in #770 
 feat(mcp): clamp response budget under the live MCP host token cap by @RaghavChamadiya in #771 
 feat(mcp): answer-by-union for homonym symbols in get_answer by @RaghavChamadiya in #772 
 feat(core): shared agent-transcript layer core/sessions by @RaghavChamadiya in #774 
 feat(core): mine durable decisions from agent session transcripts by @RaghavChamadiya in #775 
 feat: relevance-ranked decision delivery, SessionStart + edit-time injection with usage feedback by @RaghavChamadiya in #776 
 feat(cli): shared hook efficacy ledger + read-after-served adoption KPI by @RaghavChamadiya in #777 
 feat(mcp): ground get_answer synthesis in the body it serves; slim low-confidence misses by @RaghavChamadiya in #778 
 feat(mcp): ground data-shape questions in the field set mined from source by @RaghavChamadiya in #779 
 feat(mcp): surface alias keys a documented data-shape omits by @RaghavChamadiya in #780 
 feat(generation): FAQ-weighted docs budget tilts depth toward asked-about modules by @RaghavChamadiya in #781 
 Fix CI: track widened augment matcher in hook config tests by @RaghavChamadiya in #782 
 docs: hooks guide + "learns from your usage" section by @RaghavChamadiya in #784 
 feat(coverage): per-test contexts ingestion substrate (test-to-code map) by @RaghavChamadiya in #789 
 feat(coverage): persist the per-test test-to-code map + one ingestion entry point by @RaghavChamadiya in #790 
 feat(coverage): repowise impacted-tests command by @RaghavChamadiya in #792 
 chore: use full AGPL-3.0 license text so GitHub detects it by @RaghavChamadiya in #794 
 feat(coverage): coverage-backed missing-test signal by @RaghavChamadiya in #793 
 fix(update): persist wiki_symbols on incremental updates by @RaghavChamadiya in #795 
 fix(mcp): verify symbol bounds before serving live slices in get_answer by @RaghavChamadiya in #796 
 fix(search): lead hybrid results with concept pages for prose queries by @RaghavChamadiya in #797 
 feat(docker): lean MCP-only image for MCP hosts and directories by @RaghavChamadiya in #800 
 chore(glama): add glama.json to claim the MCP server listing by @RaghavChamadiya in #802 
 feat(answer): flow-shaped answers via graph path between named endpoints by @RaghavChamadiya in #804 
 fix(update): persist graph_edges on incremental update by @RaghavChamadiya in #806 
 fix(graph): keep max confidence on edge upsert by @RaghavChamadiya in #807 
 feat(mcp): forgive get_symbol(id=) and ground a hedged get_answer on the served body by @RaghavChamadiya in #783 
 Explain the agent-authorship share on the contributors strip by @swati510 in #799 
 feat(health): deduct open performance findings from the performance score by @swati510 in #801 
 feat: agent co-author detection + derived decision scope by @swati510 in #803 
 fix(graph): execution-flow picker on the module overview; hierarchical layout guardrails by @swati510 in #805 
 test(graph): type-complete node fixtures in graph-flow tests by @swati510 in #808 
 test: fix two stale unit tests failing on main CI by @swati510 in #809 
 release: v0.31.0 - coverage test intelligence, decisions from agent sessions, grounded get_answer by @RaghavChamadiya in #810 
 
 Full Changelog : v0.30.0...v0.31.0