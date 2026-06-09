---
id: inbox_5c669abf
date: 2026-06-09
source_ref: "[[00-inbox/2026-06-09/2200-gitnexus-releases-v1-6-7-8536]]"
title: "v1.6.7"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7
source: gitnexus-releases
published_at: 2026-06-09T21:05:55+00:00
fetched_at: 2026-06-09T22:04:18.470096+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 1.6.7 發布，核心突破是 Toolchain-free tree-sitter install：c、dart、proto、kotlin、swift grammars 現內置預構建本地二進制（覆蓋 linux/darwin/win32 × x64/arm64 六平台組合，每個 .node load 都用提交的 SHA256SUMS 和 SLSA build provenance 驗證），新安裝時無需 C/C++ toolchain。新增 gitnexus uninstall command，可 idempotent 反向執行 setup（移除 MCP server entries、skills、hooks），支持 --force 執行或 dry-run。MCP list_repos 添加分頁支持（limit/offset），避免 LLM token 限制導致的陣列截斷。C++ 改進包括 inheritance-lattice member lookup（dominance hiding、ambiguous-base suppression、virtual-diamond deduplication）。引入 Taint/PDG substrate (M0)，為可靠 taint analysis 奠基。MCP query enrichment 實現 batching（N+1 round-trips 優化至 2–3 WHERE IN queries）。"
key_points:
  - "Toolchain-free tree-sitter：預構建二進制消除 C/C++ toolchain 依賴（6 platform/arch 組合，SLSA provenance 驗證）"
  - "gitnexus uninstall command：完整反向 setup，idempotent 且 JSONC-preserving，支持 dry-run"
  - "MCP list_repos pagination + query enrichment batching：避免 token 截斷，N+1 優化為 2–3 queries"
tags: [gitnexus, tree-sitter, toolchain-free, mcp, taint-analysis]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v1.6.7

GitNexus 1.6.7 發布，核心突破是 Toolchain-free tree-sitter install：c、dart、proto、kotlin、swift grammars 現內置預構建本地二進制（覆蓋 linux/darwin/win32 × x64/arm64 六平台組合，每個 .node load 都用提交的 SHA256SUMS 和 SLSA build provenance 驗證），新安裝時無需 C/C++ toolchain。新增 gitnexus uninstall command，可 idempotent 反向執行 setup（移除 MCP server entries、skills、hooks），支持 --force 執行或 dry-run。MCP list_repos 添加分頁支持（limit/offset），避免 LLM token 限制導致的陣列截斷。C++ 改進包括 inheritance-lattice member lookup（dominance hiding、ambiguous-base suppression、virtual-diamond deduplication）。引入 Taint/PDG substrate (M0)，為可靠 taint analysis 奠基。MCP query enrichment 實現 batching（N+1 round-trips 優化至 2–3 WHERE IN queries）。

### 重點
- Toolchain-free tree-sitter：預構建二進制消除 C/C++ toolchain 依賴（6 platform/arch 組合，SLSA provenance 驗證）
- gitnexus uninstall command：完整反向 setup，idempotent 且 JSONC-preserving，支持 dry-run
- MCP list_repos pagination + query enrichment batching：避免 token 截斷，N+1 優化為 2–3 queries

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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

</details>