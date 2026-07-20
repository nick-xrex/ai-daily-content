---
id: inbox_d408f17f
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.33.0"
author: "github-actions[bot]"
published_at: 2026-07-18T06:44:45+00:00
fetched_at: 2026-07-18T23:18:59.134045+00:00
content_hash: "63d5d7521f82d0dc35e902b55835017fc7fbabf7261c61bcc6319728706e41b7"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.33.0

What's Changed 
 
 fix(mcp): harden code-rationale git-grep for macOS and color configs by @austintraver in #825 
 fix(answer): live-grep fallbacks respect gitignore and exclude_patterns by @swati510 in #856 
 test(mcp): assert get_symbol advertises id in its generated schema by @swati510 in #857 
 feat(coverage): surface coverage-backed tests_to_run in get_risk PR directive by @RaghavChamadiya in #859 
 fix: separate docs pointer from sync pointer to fix update --docs drift by @jyotirmya17 in #849 
 feat(git): attribute commits from agent-trace records by @RaghavChamadiya in #861 
 feat(answer): rescue un-named flow endpoints via graph-neighborhood re-rank by @swati510 in #864 
 feat(docs): graph-derived related pages with self-healing backfill by @RaghavChamadiya in #871 
 feat(git): line-level AI provenance and per-commit model id from agent-trace by @RaghavChamadiya in #866 
 feat(docs): self-repair for hallucinated symbol refs, cross-reference prompt discipline, repo-wide link resolution on updates by @RaghavChamadiya in #872 
 feat(mcp): make get_conformance and generate_refactoring_code opt-in by @RaghavChamadiya in #875 
 fix(mcp): resolve health repository from scoped session by @Real5K in #865 
 fix(server): use sync mode for webhook jobs by @Sanjays2402 in #848 
 fix(tests): tolerate workspace-tool parenthetical in MCP surface-count regex by @RaghavChamadiya in #876 
 fix: normalize decision staleness timestamps by @pollychen-lab in #877 
 feat(overview): docs counts with AI/auto split, denser health card by @RaghavChamadiya in #879 
 feat(ui): visual hierarchy pass on the Overview by @RaghavChamadiya in #882 
 feat(ui): make Attention Needed a triage panel again by @RaghavChamadiya in #883 
 Fix #648 : Wire TsconfigResolver in CLI commands by @kishansaaai in #675 
 feat(dead-code): eliminate systematic false-positive classes by @RaghavChamadiya in #886 
 fix(answer): serve substance on the gated low-confidence path; unpin cached misses by @swati510 in #887 
 fix(answer): never silently drop synthesis when a usable API key exists by @swati510 in #888 
 feat(mcp): add get_why to the lean profile; present get_answer as the entry point by @swati510 in #889 
 fix: security scan reads real source; guard repo-root detection by @RaghavChamadiya in #890 
 perf: direct self-call resolution and cached pagerank for cascade ordering by @RaghavChamadiya in #891 
 perf: skip re-embedding pages reused verbatim from prior runs by @RaghavChamadiya in #892 
 perf(health): remove repo-sized per-file work from the refactoring detectors by @RaghavChamadiya in #893 
 feat(risk): add --exclude flag, .riskignore support, and get_change_r... by @barrcodes in #867 
 perf: concurrent analysis phases and parallel incremental re-ingest by @RaghavChamadiya in #894 
 perf(update): converge init- and update-built graphs so the centrality cache hits by @RaghavChamadiya in #895 
 fix: route coverage discovery and repo pre-scan through the shared pruned walk by @RaghavChamadiya in #897 
 perf(hints): feed dynamic-hint extractors from the traversed file list by @RaghavChamadiya in #898 
 fix(change-risk): harden get_change_risk and align it with the MCP tool conventions by @RaghavChamadiya in #899 
 fix(answer): gated-path excerpts died to a silently-swallowed AttributeError by @swati510 in #896 
 feat(agents): bring AGENTS.md to CLAUDE.md tool-surface parity and sync the tool table by @RaghavChamadiya in #900 
 docs(readme): count ten MCP tools, fix the coverage example, tighten Code Health by @RaghavChamadiya in #901 
 fix: restore friendly revspec error in changed_lines and register the codex change-review skill by @RaghavChamadiya in #902 
 feat(change-risk): line-level impacted tests in get_change_risk by @RaghavChamadiya in #903 
 perf(persist): batch end-of-run wiki-page upserts by @RaghavChamadiya in #904 
 fix(resolver): follow Python/JS wildcard re-exports in call resolution by @RaghavChamadiya in #905 
 chore: remove verified dead code across CLI, core, server, and web by @RaghavChamadiya in #906 
 fix: preserve last_docs_commit pointer during index-only updates (Fixes #873 ) by @jyotirmya17 in #878 
 fix(telemetry): classify CLI usage errors separately from failures by @RaghavChamadiya in #907 
 fix(restyle): raise a usage error for an unknown style argument by @RaghavChamadiya in #908 
 release: v0.33.0 — agent-trace provenance, self-healing docs, change-risk maturity, indexing perf by @RaghavChamadiya in #909 
 
 New Contributors 
 
 @Sanjays2402 made their first contribution in #848 
 @pollychen-lab made their first contribution in #877 
 @barrcodes made their first contribution in #867 
 
 Full Changelog : v0.32.0...v0.33.0