---
id: inbox_0a582d42
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.35.0"
author: "github-actions[bot]"
published_at: 2026-07-24T11:38:57+00:00
fetched_at: 2026-07-27T01:23:08.146273+00:00
content_hash: "1147b05bcdc9fca8a10e763747257d91941d206da64bb6cad482e92c6224bf91"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.35.0

What's Changed 
 
 fix(ui): render the bug-fix history these surfaces already receive by @RaghavChamadiya in #960 
 docs: lead with the numbers, restore the five-layer table, fix serve ports by @RaghavChamadiya in #961 
 fix(workspace): scope file count and top-language queries to node_type='file' by @Nehant14 in #952 
 fix(ui): render the fix history the file page already receives by @RaghavChamadiya in #966 
 feat(files): mark which symbols in a file keep getting fixed by @RaghavChamadiya in #968 
 feat(security): add repowise security scan --history for full git-history secret scanning by @Ayush7614 in #821 
 fix(server): resolve workspace repos in chat tool calls by @RaghavChamadiya in #971 
 feat(generation): render every wiki page type without an LLM by @RaghavChamadiya in #972 
 fix: keep data-shape grep paths color-stable by @pollychen-lab in #860 
 fix(generation): make wiki page ids stable across runs by @RaghavChamadiya in #974 
 feat(cli): make init --index-only produce a complete wiki, no key, no spend by @RaghavChamadiya in #975 
 fix(cli): keep the index-only wiki honest, current and free by @RaghavChamadiya in #976 
 feat(cli): add repowise generate for scoped, cost-gated wiki generation by @RaghavChamadiya in #978 
 feat(cli): rank generate coverage and add an interactive chooser by @RaghavChamadiya in #979 
 feat(ui): move governing decisions on file page into dedicated tab ( #973 ) by @akshatmalik-bruh in #977 
 feat(parser): add adaptive TSX grammar fallback for .ts files containing JSX by @akshatmalik-bruh in #967 
 test(claude-plugin): add structural parity tests mirroring test_codex_plugin by @Ayush7614 in #963 
 feat(codex): add code-health skill for Codex plugin parity by @Ayush7614 in #962 
 fix(ollama): wrap timeout/connection errors so they retry by @dev-ploy in #829 
 chore: make .gitignore OSS-safe and fix two dead doc links by @RaghavChamadiya in #981 
 refactor(generate): extract the scoped-generation engine into core by @RaghavChamadiya in #982 
 feat(server): expose scoped page generation over HTTP by @RaghavChamadiya in #983 
 feat(server): authenticate the SSE job stream and mirror provider keys to repo .env by @RaghavChamadiya in #984 
 fix(server): resolve the provider-key repo by id, not the request path by @RaghavChamadiya in #985 
 feat(coupling): make the change-coupling page interactive and surface it on Overview by @RaghavChamadiya in #986 
 fix(dead-code): correct the findings table and give it an AI prompt, links and reasons by @RaghavChamadiya in #990 
 feat: provider key settings and per-page AI docs generation from the reader by @RaghavChamadiya in #988 
 feat: bulk AI doc generation and provenance surfaces in the web UI by @RaghavChamadiya in #991 
 fix(openai): clamp temperature to 1 for GPT-5+ reasoning models by @IlyaSavich in #989 
 feat(dead-code): rebuild the findings table on the shared table primitive by @RaghavChamadiya in #992 
 feat(dead-code): one confidence scale, a reopen path, and shared primitives by @RaghavChamadiya in #993 
 feat: coverage picker for web bulk documentation generation by @RaghavChamadiya in #994 
 feat: deterministic template wiki for workspace and keyless server indexing by @RaghavChamadiya in #999 
 fix(update): report deferred workspace docs runs honestly by @RaghavChamadiya in #1000 
 fix(init): render the template wiki when no provider is configured by @RaghavChamadiya in #1001 
 fix(init): degrade unanswerable prompts instead of ending the run by @RaghavChamadiya in #1002 
 feat(init): add --docs, and stop telling agents a key is required by @RaghavChamadiya in #1003 
 fix(update): clean up stale .update.pending markers by @RaghavChamadiya in #1004 
 fix(server): self-heal indexed commit in overview-summary by @RaghavChamadiya in #1005 
 fix(embed): resolve the embedder from the store, not the environment by @RaghavChamadiya in #1007 
 chore: shrink demo media from ~28MB to ~7MB by @RaghavChamadiya in #1006 
 fix(wiki): page title, layer identity and deterministic file page defects by @RaghavChamadiya in #1013 
 feat(wiki): persist page hierarchy in the data model by @RaghavChamadiya in #1014 
 feat(wiki): read the stored page tree in MCP, the docs tree and breadcrumbs by @RaghavChamadiya in #1022 
 test(claude-plugin): assert commands/*.md set and frontmatter by @Ayush7614 in #1018 
 docs(examples): add examples index and discoverability links by @Ayush7614 in #1019 
 docs(claude-plugin): sync MCP tool surface and hooks with reality by @Ayush7614 in #1017 
 feat(generation): derive a concept outline deterministically, name it with an LLM by @RaghavChamadiya in #1023 
 feat(generation): concept groups replace per-directory module pages by @RaghavChamadiya in #1024 
 feat(generation): a model names the concept pages, and the tree stops documenting documentation by @RaghavChamadiya in #1025 
 feat(generation): one renderer per page type, salted structural pages by @RaghavChamadiya in #1032 
 Collapse init and generate to a single cost question by @RaghavChamadiya in #1036 
 feat: drop the template-vs-AI provenance axis from the API and UI by @RaghavChamadiya in #1037 
 feat(ui): concept-first docs navigation by @RaghavChamadiya in #1038 
 feat(refactoring): show the duplicated block in extract-helper plans by @RaghavChamadiya in #1039 
 feat(mcp): demote decision records and test pages in retrieval by @RaghavChamadiya in #1040 
 docs(commercial): list ten MCP tools including get_change_risk by @Ayush7614 in #1031 
 fix(dead-code): align CLI/REST min_confidence default with MCP by @Ayush7614 in #1030 
 docs: fix stale MCP tool counts in package READMEs by @Ayush7614 in #1028 
 docs(cli): document repowise security in CLI_REFERENCE by @Ayush7614 in #1026 
 feat(claude-plugin): add coverage and impacted-tests slash commands by @Ayush7614 in #1029 
 Concept pages read as subsystem docs, plus parent-dir overview pages by @RaghavChamadiya in #1043 
 docs: align wiki generation docs with the single-renderer model by @RaghavChamadiya in #1044 
 feat(mcp): lead subsystem questions with their concept page by @RaghavChamadiya in #1046 
 fix(mcp): resolve refactoring alias against its scoped session ( #880 ) by @swati510 in #1045 
 feat(upgrade): recommend a re-index for wikis predating the subsystem pages by @RaghavChamadiya in #1035 
 docs: correct generate written-set and log concept-tree changes by @RaghavChamadiya in #1047 
 docs: correct onboarding collection slot count in docstrings by @RaghavChamadiya in #1048 
 fix(ui): stop counting tombstoned pages in the docs tree by @RaghavChamadiya in #1049 
 fix(cli): exclude tombstoned pages from status and export listings by @RaghavChamadiya in #1050 
 feat(cli): include hierarchy columns in JSON wiki export by @RaghavChamadiya in #1051 
 fix(generation): place parent-dir rollup pages under their children's layer by @RaghavChamadiya in #1052 
 fix(ui): keep table-of-contents keys unique across repeated headings by @RaghavChamadiya in #1053 
 feat(ollama): support disabling reasoning by @austintraver in #1009 
 chore(deps): consolidate dependency security bumps by @RaghavChamadiya in #1054 
 fix(upgrade): resync bundled changelog with docs/CHANGELOG.md by @RaghavChamadiya in #1055 
 feat(mcp): get_context surfaces concept-tree position by @RaghavChamadiya in #1056 
 feat(codex): bring skill guidance to Claude parity by @Ayush7614 in #1016 
 feat(mcp): search_codebase fuses FTS + vector via RRF by @RaghavChamadiya in #1057 
 fix(deps): restore lockfile packages pruned by the security refresh by @RaghavChamadiya in #1059 
 fix(update): recover idle files' time-decayed health on update ( #728 ) by @swati510 in #1061 
 fix(mcp,test): green main CI — trim search_codebase docstring, fix concept key assertion by @RaghavChamadiya in #1062 
 generate onboards a provider like init when a docs run needs one by @RaghavChamadiya in #1060 
 fix(server): normalize repository sort timestamps by @Sanjays2402 in #1058 
 fix(ui): mark Button as a client component by @RaghavChamadiya in #1063 
 release: v0.35.0 — one wiki renderer, keyless template wikis, and repowise generate by @RaghavChamadiya in #1064 
 
 New Contributors 
 
 @Nehant14 made their first contribution in #952 
 @akshatmalik-bruh made their first contribution in #977 
 @dev-ploy made their first contribution in #829 
 @IlyaSavich made their first contribution in #989 
 
 Full Changelog : v0.34.0...v0.35.0