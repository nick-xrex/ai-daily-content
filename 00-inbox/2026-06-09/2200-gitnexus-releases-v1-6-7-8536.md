---
id: inbox_5c669abf
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7"
author: "github-actions[bot]"
published_at: 2026-06-09T21:05:55+00:00
fetched_at: 2026-06-09T22:00:22.501566+00:00
content_hash: "8536a082e5b435023a1d130462a86bbbe2cbb24e53124cf89f83bf065b559e25"
lang: en
caption_quality: None
raw: true
topics: []
---

# v1.6.7

Added 
 
 Toolchain-free tree-sitter install — the c , dart , proto , kotlin , and swift grammars now ship vendored native prebuilds (six platform/arch each — linux/darwin/win32 × x64/arm64, every .node load-and-parse verified with committed SHA256SUMS and SLSA build provenance), so a fresh install no longer requires a C/C++ toolchain; kotlin moved off its optionalDependency into the vendored path, dart / proto keep a source-build fallback when no prebuild matches, and a registry-parameterized CI workflow builds, load-validates, and vendors the binaries ( #2113 , #2125 , #2110 ) 
 gitnexus uninstall — reverses gitnexus setup target-by-target, surgically removing GitNexus MCP server entries (Cursor, Claude Code, Antigravity, OpenCode, Codex), installed skill directories, and Claude Code / Antigravity hook entries with their bundled scripts; idempotent, JSONC-preserving, dry-run by default with --force to apply ( #2062 , #2060 ) 
 MCP list_repos pagination — bounded limit / offset paging so clients can reliably enumerate every indexed repository instead of having the unpaginated array truncated by LLM token limits; the result is now a { repositories, pagination } object (page until pagination.hasMore is false), with deterministic (lower-cased name, path) ordering ( #2120 , #2119 ) 
 C++ inheritance-lattice member lookup — receiver members now resolve through the inheritance lattice with dominance hiding, ambiguous-base suppression, virtual-diamond deduplication, and overload ranking, and class-scope using Base::member declarations are no longer mistaken for namespace imports ( #2077 , #1891 ) 
 Taint/PDG substrate (M0) — foundational graph schema and pipeline seams for reliable taint analysis on a PDG-expandable substrate: the BasicBlock node label and CFG / REACHING_DEF / TAINTED / SANITIZES / TAINT_PATH relationship types (round-tripped through the bulk-COPY path), a phase-registry seam ( registerPhase / enabledWhen ) generalising the graph-phase opt-in guard, and a per-language source/sink/sanitizer config registry. All additive and inert — no phase emits the new nodes/edges yet and a default analyze run is byte-identical to before ( #2092 , #2080 ) 
 
 Fixed 
 
 Optional grammars lazy-loaded so analyze never crashes when one is missing — the swift/dart/kotlin query.ts modules no longer statically import their tree-sitter binding at module load, so a missing optional grammar can no longer abort gitnexus analyze (or the MCP server, doctor , and .githooks auto-reindex) with ERR_MODULE_NOT_FOUND regardless of the repo's actual languages; grammars now resolve lazily at first use inside the worker, GITNEXUS_SKIP_OPTIONAL_GRAMMARS is honored at runtime, the scope-resolution phase excludes unavailable-language files, and skip diagnostics/precheck globs were corrected ( #2101 , #2091 , #2093 ) 
 tree-sitter-kotlin optional-grammar install — install now fails soft when no C/C++ toolchain is present, emitting one clear warning and always exiting 0 (mirroring the Swift/Dart/Proto probes) instead of breaking gitnexus install; optional-grammar/toolchain docs corrected to include Kotlin ( #2110 , #2107 ) 
 CLI image FTS keyword search — the full-text-search extension is now baked into the CLI Docker image so a containerized serve does offline keyword search instead of silently degrading to vector-only ( #2108 ) 
 
 Changed 
 
 Tree-sitter prebuild CI matrix greened and made re-run-safe — dropped the broken -t 22 flag from the prebuildify invocation that crashed every matrix job ( v.indexOf is not a function ; N-API prebuilds are Node-version-agnostic, so no target is needed) ( #2121 ), cleared npm-bundled prebuilds/ before prebuildify so the host tuple is detected (not a stray win32-x64 ) and source-built the tree-sitter runtime peer on linux-arm64 where upstream ships no prebuild ( #2122 ), and switched the vendor-prebuilds push to git push --force so re-running a workflow no longer fails with a stale-lease rejection ( #2123 ) 
 
 Performance 
 
 MCP query enrichment batched — the query tool now batches its per-symbol enrichment lookups (3N sequential pool round-trips collapsed to 2–3 WHERE n.id IN $nodeIds queries), cutting N+1 round-trips with byte-identical output ( #2108 ) 
 
 Chore / Dependencies 
 
 @ladybugdb/core bumped 0.17.0 → 0.17.1 in /gitnexus ( #2098 ) 
 Claude plugin manifests synced to the release version — bumped plugin.json and the gitnexus marketplace.json entry to match the published npm version (stale 1.3.x manifests had blocked marketplace updates), added a Vitest guard asserting all three manifests advertise one version, and documented the sync step in CONTRIBUTING.md ( #2090 )