---
id: inbox_4bb47af3
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.6"
author: "github-actions[bot]"
published_at: 2026-06-08T09:27:22+00:00
fetched_at: 2026-06-08T18:00:44.724657+00:00
content_hash: "b14565c707ce668cf4cf6649a004cf0e88652304390860a483cf450282c10a0f"
lang: en
caption_quality: None
raw: true
topics: []
---

# v1.6.6

GitNexus 1.6.6 is a large release — ~190 PRs since v1.6.5 (50 features, 96 fixes, 6 performance overhauls). The theme: scale and breadth — GitNexus now indexes Linux-kernel-scale repositories, every language runs on one unified resolution engine, and it traces API calls across service boundaries. 
 
 Drop-in upgrade — no breaking changes . npm i -g gitnexus@1.6.6 and re-run gitnexus analyze . 
 
 ✨ Highlights 
 🧠 Scope-resolution migration complete across every language 
 Call and inheritance resolution now runs on the unified registry-primary engine (RFC #909 ) for the entire language matrix. Rust, JavaScript, Ruby, Swift, Vue SFC, Dart, COBOL, and Kotlin all migrated this release, and Java reached 100% parity . The payoff: more accurate cross-file call graphs, inheritance edges, and type resolution — with consistent behaviour across languages. 
 ⚡ Indexes Linux-kernel-scale repositories 
 A major scalability overhaul ( #1983 , #2038 ) lets gitnexus analyze handle massive codebases without running out of memory: a parallel worker-pool parse , an O(n2)→indexed finalize pass, and a RAM-aware memory wall for scope resolution. On top of that, scope-capture was linearized O(n2)→O(n) across all languages ( #1918 , #1915 ) and C++ ADL lookup is now indexed once instead of rescanned per call-site ( #1990 ) — together cutting analyze time and peak memory dramatically on large repos. 
 🗺️ Cross-service API call graphs 
 GitNexus now traces HTTP requests across service boundaries. Route and consumer contracts are extracted for Spring (Java/Kotlin), OpenFeign , FastAPI (including include_router(prefix=...) and Depends() ), gRPC , and frontend HTTP clients — connecting "who calls this endpoint" across repositories and languages. 
 🧹 Legacy resolution engine removed (Ring 4) 
 With every language migrated, the old call-resolution DAG, heritage processor, tiered-lookup resolution context, and shadow-mode parity harness were deleted ( #942 , #943 , #944 ) — a large code reduction and a single, predictable resolution pipeline. 
 🔬 Language coverage &amp; correctness 
 Parsing-layer coverage gaps were closed across the whole matrix (umbrella #1919 ) — Java, PHP, COBOL, Rust, Python, JS/TS, and Ruby — alongside deep C++ (ADL, templates, overload ranking, SFINAE), C# , Kotlin , and Go resolution fixes. 
 🛠️ Developer experience 
 
 .gitnexusrc project config + analyze --default-branch ( #243 , #1996 ) 
 A devcontainer for the Claude / Codex / Cursor CLIs ( #1875 ) 
 Web viewer : new Tree View and Circles View ( #1799 ), GitLab repo URLs ( #1565 ), and full UI/CLI internationalization ( #1748 ) 
 Wiki : local Claude/Codex/opencode providers ( #1769 , #2039 ) and multilanguage wikis via --lang ( #1613 ) 
 DeepSeek V4 support ( #1594 ); self-healing worker pool ( #1741 ); plus many MCP, Windows, and LadybugDB reliability fixes 
 
 
📋 Full categorized changelog (every change, grouped)
 Added 
 
 Scope-resolution (RFC #909 ) migrations completed across the language matrix — Rust ( #1639 ), JavaScript ( #1640 ), Ruby ( #1831 ), Swift ( #937 , #1948 ), Vue SFC ( #940 , #1950 ), Dart ( #939 , #1970 ), COBOL ( #941 , #1835 , #1842 ), and Kotlin ( #1727 , #1746 , #1782 ) now run on the registry-primary path; Java reached 100% scope-resolution parity and joined MIGRATED_LANGUAGES ( #1805 ); per-language progress reporting added to the scope-resolution phase ( #1813 ) 
 HTTP route &amp; consumer contract extraction (group mode) — Spring interface routes attributed to controllers ( #1743 ); named/positional Java Spring route args ( #1834 ); Kotlin Spring HTTP route, consumer, and WebClient long-form extraction ( #1849 , #1855 , #1884 ); Java HTTP consumer contracts ( #1872 ); OpenFeign @RequestLine consumer contracts incl. plain interfaces without @FeignClient ( #1904 , #1917 ); FastAPI include_router(prefix=...) cross-file routes ( #1877 ); indirect call patterns via FastAPI Depends() and frontend HTTP consumers ( #1852 ); gRPC consumer FQN derivation from Java imports for client-jar consumers ( #1889 ) 
 C++ overload &amp; template resolution — operator-call resolution ( #1754 ), template partial ordering ( #1885 ), user-defined conversion ranking ( #1829 ), nullptr/ellipsis pointer conversion ranks ( #1708 ), SFINAE filter ( #1623 ), expanded type_traits constraint registry ( #1648 ), structured resolver-suppression outcomes ( #1785 ), function-type ADL entities ( #1822 ), and a parameter-type class sidecar ( #1642 ) 
 Go enhancements — structural interface implementation inference ( #1966 ) and a builtInNames set for the Go language provider ( #1886 ) 
 Self-healing worker pool — automatic worker replacement plus deferred-resolution observability and verbose progress logging ( #1741 , #1773 , #1947 ) 
 .gitnexusrc config file and gitnexus analyze --default-branch ( #243 , #1996 ) 
 CLI / MCP impact ergonomics — --uid/--file/--kind disambiguation flags ( #1907 , #1914 ), limit/offset/summaryOnly pagination on the impact tool ( #1818 ), and a per-symbol processes field on byDepth items ( #1867 ) 
 gitnexus analyze --repair-fts — enforces FTS verification with hardened repair safeguards ( #1720 ) 
 Web viewer — Tree View and Circles View ( #1799 ), GitLab repository URLs ( #1565 ), GITNEXUS_BACKEND_URL env var for Docker deployments ( #1286 ), and web + CLI internationalization ( #1748 ) 
 Wiki — local Claude/Codex providers ( #1769 ), an opencode local provider ( #2039 ), and gitnexus wiki --lang &lt;lang&gt; for multilanguage wiki generation ( #1613 ) 
 detect-changes git-worktree support ( #1654 ) 
 DeepSeek V4 API support ( #1594 ) 
 Devcontainer for the Claude / Codex / Cursor CLIs ( #1875 ) and antigravity integration setup + hook adapter ( #1730 ) 
 Object-literal methods linked to exported bindings ( #1718 ) 
 eval-server --host for a user-configured bind IP ( #1667 ) 
 PR reviewer swarm agents ( #1851 ) 
 tree-sitter node-type/field validation gate — validates against the grammar and removes dead literal handling ( #1937 ) 
 
 Fixed 
 
 Parsing-layer coverage gaps closed across the language matrix (umbrella #1919 ) — remaining open gaps ( #2072 ) plus Java F35/F38/F41 ( #1928 , #2045 ), PHP F53/F54/F55 ( #1931 , #1989 ), COBOL F17–F23 ( #1925 , #1959 ), Rust F66/F68/F71/F72 ( #1934 , #1974 ), Python F57/F58/F61 ( #1932 , #1964 ), JS/TS F44/F83/F85/F86/F87 ( #1929 , #1968 ), and Ruby F62 ( #1933 , #1972 ) 
 Fully-qualified nested-type identity for C++ and Ruby — distinct nodes for union-, anonymous-namespace-, and same-tail-nested types ( #1978 , #1981 , #2004 , #2005 ); cross-namespace same-tail inheritance bases resolved ( #1993 , #2005 ); Ruby same-tail nested mixin modules qualified with IMPLEMENTS routed by scope ( #1991 , #2006 ); shared codec for __heritage__ / __property__ markers ( #1994 , #2007 ); graph nodes materialized for scoped class/module/impl declarations ( #1975 , #1977 ); generic Rust inherent-impl methods owned through the mod-qualified Impl node ( #1992 , #2003 ) 
 C# resolution &amp; memory — global-namespace typeBindings O(files2) OOM eliminated ( #1871 , #1954 ) and namespace-siblings OOM with worker-path re-parse removed ( #1905 ); qualified/alias constructor names, :base / :this initializers, and generic type-arg stripping ( #2046 ); primary-base receiver type normalization ( #2036 ); spurious IMPORTS edges from ungated using resolution stopped ( #1881 , #1908 ) 
 C++ dependent-base and member lookup — resolution across nested/inline namespaces ( #1634 , #1814 ), base-specifier qualifier threading ( #1815 , #1819 ), call-site types threaded into qualified member lookup ( #1632 , #1810 ), variadic pack dependent lookup ( #1909 ), uninitialized multi-declarators ( #1965 ), and typedef-enum / anonymous-struct declarations ( #1941 ) 
 Kotlin type resolution — smart-cast refinement for when/is and if/is ( #1758 , #1774 ), overload target-id by parameter types ( #1761 , #1777 ), cross-file iterable return propagation ( #1759 , #1775 ), method-chain fixpoint receiver types ( #1760 , #1776 ), virtual dispatch via constructor type override ( #1762 , #1778 ), interface default-method dispatch via implements-split MRO ( #1763 , #1779 ), and default-parameter arity detection ( #2034 ) 
 Go declarations — multi-name declaration capture ( #2032 ), fixed-array parameter binding normalization ( #1988 ), and generic composite-literal constructor inference F33 ( #1976 ) 
 Rust / PHP / Vue / Java parsing — Rust struct_expression name pattern split ( #2051 ); PHP import decomposition, namespace-less .phtml module scopes, and Blade-template exclusion ( #1801 , #1790 , #1989 ); Vue JSDoc, dual-script merge, and lang plumbing F89/F90/F92 ( #1936 , #2050 ); Java inherited RequestMapping prefix deduplication ( #2057 ) and same-module type resolution for duplicate FQNs ( #1712 ) 
 TypeScript — HOC pattern false positives fixed with export default HOC support ( #1943 ) and suffix-index reuse in the scope resolver ( #1840 ) 
 Inheritance on the worker path — all languages' inheritance migrated to scope-resolution in worker mode ( #1951 , #1956 ); centralized heritage supertype matching ( #1921 , #1922 , #1940 ); File-&gt;Member DEFINES edges skipped for class members ( #1949 ); phantom Function defs for array-method callbacks no longer emitted ( #1906 ) 
 MCP — sibling-clone repo-ID collisions prevented and generated MCP tool names corrected ( #2067 ); orphan processes avoided by handling stdin close/end and the startup race ( #2049 ); duplicate-name repo resolution disambiguated for worktrees ( #1753 ); Windows setup fallback when global gitnexus resolves to a non-spawnable shim ( #1694 ) 
 Worker pool — resilient zero-copy ingestion worker pool prevents analyze hangs on TS-root-scale loads ( #1693 ); cache-hit native workers no longer abort ( #1751 , #1833 ); worker-pool docs drift corrected and worker-side stack surfaced on crash ( #2068 , #2070 ) 
 LadybugDB — FTS loaded in the Windows read pool ( #2040 ) and probed-then-loaded on Windows ( #1690 , #1692 ); non-ASCII KuzuDB paths resolved on Windows ( #1811 , #1817 ); WAL corruption detected in schema init with recovery surfaced ( #1647 , #1650 ); WAL checkpoint-threshold control ( #1772 ); init lock skipped for read-only opens ( #1783 , #1784 ); serve kept stable when sidecars are missing ( #1747 ) 
 Server / API — gitnexus serve startup restored under Express 5 ( #1749 ); /api/graph , /api/search , /api/grep opened read-only ( #1686 ); native read-only enforcement and prepared statements for Cypher query paths ( #1655 ); eval-server localhost binding left to the OS ( #1722 ) 
 Embeddings — local ONNX runtime guarded on macOS Intel before the transformers.js import ( #1987 ) 
 Web agent — Nexus AI agent system prompt aligned with registered tools ( #1984 ) and the agent stopped cleanly on user Stop ( #1820 ) 
 Group / contracts — HTTP graph and source contracts unioned ( #1709 ); httpx AsyncClient alias imports detected ( #1687 ); Node gRPC loadPackageDefinition gate no longer matches every member call ( #1916 ); manifest/workspace extraction moved before closeLbug ( #1802 , #1807 ) 
 Hooks / install — gitnexus resolved on PATH via a pure-Node, all-OS scan ( #1938 , #1980 ); offline-first extension installs ( #1161 ); actionable error and docs for the pnpm dlx / pnpx native-load crash ( #307 , #1967 ); onnxruntime-common declared as a runtime dependency ( #2074 ); vendored grammars materialized to fix Windows EPERM ( #1728 , #1729 ) 
 CLI — missing LadybugDB native binary detected at startup with actionable guidance ( #835 , #1837 ); --no-stats applied to the keep-marker stats line ( #1706 , #1765 ); skipped large-file paths surfaced by default ( #1659 , #1661 ); build.js skipped when running outside the monorepo ( #1795 , #1816 ); auto-heap raised to 16 GB with tightened cross-platform OOM guidance for UE5-scale repos ( #1652 ) 
 Wiki — hidden 60s default timeout removed with timeout/retry flag validation and surfaced timeout errors ( #1

[... truncated for safety ...]