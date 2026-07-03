---
id: inbox_aaf4eef6
date: 2026-07-02
source_ref: "[[00-inbox/2026-07-02/2200-gitnexus-releases-rc-1029a8ddd73f37237d2c5c13168ee724dcd8d-751d]]"
title: "rc/1029a8ddd73f37237d2c5c13168ee724dcd8dd91: feat: add Spring DI resolver for @Autowired List&lt;T&gt; injection (#2200)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F1029a8ddd73f37237d2c5c13168ee724dcd8dd91
source: gitnexus-releases
published_at: 2026-07-02T16:49:46+00:00
fetched_at: 2026-07-02T22:07:14.310863+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 發布了 Spring DI resolver，實現對 @Autowired List<T> injection 的支持，解決所有 P0/P1 findings。核心改進是線程化原始泛型字段類型（rawDeclaredType）使 Spring DI 匹配工作於真實提取輸出，而非先前因類型去掉泛語而失效。新增基於注解門控的 DI 候選篩選（@Autowired/@Inject，排除 @resource），以及針對嵌套泛型和 bounded wildcards 的深度感知型 collection-type parser。實現框架中立的 DI 階段設計，將 Spring 特定匹配器移至語言範疇。整體新增 8 個單元測試和 end-to-end 集成測試，Property node schema 升級至 v10。"
key_points:
  - "線程化 rawDeclaredType 保留泛型信息，使 Spring DI 匹配對真實提取輸出有效（先前實現因 declaredType 去掉泛語導致無法匹配）"
  - "注解門控識別 @Autowired/@Inject 注解的集合字段，排除 @resource（JSR-250 按名解析單個 bean，與 INJECTS 的扇出行為矛盾）"
  - "深度感知的 Spring collection-type parser 支持嵌套泛型如 Map<Pair<A,B>, IFoo>、bounded wildcards 如 List<? extends IFoo>，透過 27 個表驅動測試確保邊界情況覆蓋"
tags: [spring-di-resolver, generic-type-threading, annotation-driven, collection-type-parsing, gitnexus]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/1029a8ddd73f37237d2c5c13168ee724dcd8dd91: feat: add Spring DI resolver for @Autowired List<T> injection (#2200)

GitNexus 發布了 Spring DI resolver，實現對 @Autowired List<T> injection 的支持，解決所有 P0/P1 findings。核心改進是線程化原始泛型字段類型（rawDeclaredType）使 Spring DI 匹配工作於真實提取輸出，而非先前因類型去掉泛語而失效。新增基於注解門控的 DI 候選篩選（@Autowired/@Inject，排除 @resource），以及針對嵌套泛型和 bounded wildcards 的深度感知型 collection-type parser。實現框架中立的 DI 階段設計，將 Spring 特定匹配器移至語言範疇。整體新增 8 個單元測試和 end-to-end 集成測試，Property node schema 升級至 v10。

### 重點
- 線程化 rawDeclaredType 保留泛型信息，使 Spring DI 匹配對真實提取輸出有效（先前實現因 declaredType 去掉泛語導致無法匹配）
- 注解門控識別 @Autowired/@Inject 注解的集合字段，排除 @resource（JSR-250 按名解析單個 bean，與 INJECTS 的扇出行為矛盾）
- 深度感知的 Spring collection-type parser 支持嵌套泛型如 Map<Pair<A,B>, IFoo>、bounded wildcards 如 List<? extends IFoo>，透過 27 個表驅動測試確保邊界情況覆蓋

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F1029a8ddd73f37237d2c5c13168ee724dcd8dd91)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

feat: add Spring DI resolver for @Autowired List injection 
 
 Addresses all P0/P1 findings from tri-review ( #2200 ): 
 
 P0: Register INJECTS in RelationshipType union (compiles) 
 P0: Rewrite execute() to emit consumer→implementation edges from graph data only 
 P1: Register in VALID_RELATION_TYPES, single-pass O(N) indexes 
 P1: Java-only gate with early exit on non-Java repos 
 P1: Update FULL_ORDER golden test 
 8 unit tests covering all edge cases 
 
 
 test: make VALID_RELATION_TYPES size assertion array-driven (no hardcoded count) 
 
 The security test hardcoded toBe(16) for the relation type count, but PR #2200 
added INJECTS, bumping it to 17. Replace the magic number with an 
EXPECTED_RELATION_TYPES array whose .length drives the size assertion, 
so future additions only need to append to the list. 
 Fixes CI failure on PR #2200 . 
 
 fix(ingestion): thread raw generic field types onto Property nodes so Spring DI matching works (review 4616076037 P0) 
 
 Production declaredType is generics-stripped by design (extractSimpleTypeName: 
List -&gt; "List"), so the spring-di phase's anchored regexes could never 
match real extraction output — the phase was a silent no-op on every real Java 
repository, while its unit tests passed against hand-built node shapes. 
 Add FieldInfo.rawDeclaredType captured verbatim from the field's type node 
(.text, generics and qualifiers preserved — same precedent as the JVM method 
extractor), thread it through both parse-worker Property sites, add it to the 
shared NodeProperties contract, and match on rawDeclaredType ONLY (no 
declaredType fallback: it can never match real data and would mask future 
plumbing regressions as quiet no-ops). 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(ingestion): gate Spring DI on real injection annotations, honest edge reason (review 4616076037 P1) 
 
 Extract Java field annotations (shared extractAnnotations helper, moved 
verbatim from the method extractor) onto Property nodes and require 
 @Autowired or @Inject before a collection field becomes an INJECTS 
candidate. Previously every edge's reason string fabricated " @Autowired " 
without any annotation ever being checked, and any plain collection field 
would have fanned out false edges once matching worked. 
 @resource is deliberately excluded: JSR-250 resolves by bean name first 
(defaulting to the field name), injecting a single named collection bean — 
the opposite of the collect-all-implementers fan-out INJECTS models. Pinned 
by a test. 
 An annotated candidate missing rawDeclaredType now logs an isDev warning 
(plumbing-contract breach signal) instead of vanishing silently. 
 SCHEMA_BUMP 9 -&gt; 10: Property nodes gained rawDeclaredType + annotations; 
warm parse caches must invalidate or the DI phase silently no-ops on 
replayed pre-upgrade nodes (the #2038 trap). 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 refactor(ingestion): framework-neutral di phase + language-scoped Spring matcher registry (review 4616076037 P1) 
 
 spring-di was the only pipeline phase naming a language in shared 
core/ingestion code (DoD.md language rule; the maintainer's direction is a 
generic DI solution). Split it: 
 
 di-extractors/spring.ts: the Spring matcher (annotation gate, collection 
type parse, @resource exclusion rationale, framework-specific reason 
payload) — language-scoped home, mirroring route-extractors/. 
 di-extractors/index.ts: DI_MATCHERS, a single-valued 
ReadonlyMap&lt;SupportedLanguages, DiFieldMatcher&gt; mirroring the 
SCOPE_RESOLVERS registry shape sanctioned by AGENTS.md. Constructor 
injection deliberately out of scope; widen to arrays only when a second 
same-language framework lands. 
 pipeline-phases/di.ts (renamed from spring-di.ts): framework-neutral — 
routes Property nodes to registered matchers by node language via a typed 
guard, then runs the unchanged reverse-index fan-out. Zero language or 
framework names remain (grep-verified). 
 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(ingestion): language- and qualified-name-scoped interface resolution for DI fan-out (review 4616076037 P2) 
 
 The interface index was built from ALL Interface nodes regardless of 
language, keyed by bare simple name with last-writer-wins overwrite — 
a polyglot repo with a TS and a Java 'Shape' could fan Java INJECTS edges 
into TypeScript classes, and two same-named Java interfaces in different 
packages silently collapsed to whichever parsed last (documented GitNexus 
bug class: #2054 , PR #1956 ). 
 Resolution is now per-language with qualifiedName as the primary key 
(Interface nodes already carry package-qualified qualifiedName); dotted 
element types resolve via qualifiedName, bare names via a per-language 
simple-name index that records ambiguity and fails CLOSED. Ambiguity skips 
are observable: DIOutput.ambiguousSkipped + an aggregated isDev debug log, 
so 'no DI fields' is distinguishable from 'all candidates ambiguous'. 
Same-package tiebreaking is a pinned, documented follow-up. 
 Order-independence pinned by running collision tests in both insertion 
orders. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(ingestion): depth-aware Spring collection-type parser for idiomatic generics (review 4616076037 P3) 
 
 The two anchored regexes silently skipped idiomatic Spring shapes: 
Map&lt;Pair&lt;A,B&gt;, IFoo&gt; (nested-generic key broke the [^,]+ split), 
List&lt;? extends IFoo&gt; / List&lt;? super IFoo&gt; (bounded wildcards), 
java.util.List (qualified wrapper), and whitespace/multi-line 
declarations. 
 Replace them with a small scanner: whitespace normalization, wrapper 
matched by last dotted segment, depth-aware top-level-comma split, wildcard 
bound stripping, and a final plain-dotted-type-name gate so anything else 
(nested-generic elements, arrays, unbounded wildcards, embedded comments, 
unbalanced brackets) fails closed. Every accept and reject is documented in 
the module docstring and pinned by 27 table-driven cases. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 test(integration): prove Spring DI end-to-end through the real pipeline (review 4616076037 P1) 
 
 Both no-op incarnations of this feature shipped with a green unit suite 
because every test hand-built the exact graph shape the phase expected — 
no test ever ran real Java source through the actual extraction pipeline. 
 Add test/integration/spring-di-pipeline.test.ts: real .java fixtures via 
runPipelineFromRepo, pinning (a) the extraction contract on the annotated 
field's Property node (declaredType 'List', rawDeclaredType 'List', 
annotations [' @Autowired ']), (b) set-equality on ALL INJECTS edges 
(exactly Consumer-&gt;FooA and Consumer-&gt;FooB; the non-annotated 'plain' 
field of the same type contributes nothing; no self-edges), and (c) a 
negative-control fixture with no injection annotations producing zero 
INJECTS edges. Either historical regression fails at least one of these. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix(incremental): register INJECTS across product surfaces + delete-before-writeback (review 4616076037 P2) 
 
 INJECTS was allowlisted in VALID_RELATION_TYPES but invisible or unhandled 
everywhere else. Register it deliberately: 
 
 REL_TYPES (gitnexus-shared schema-constants): web-side validRelType() 
otherwise silently rejects INJECTS filters (CLI/web single source of truth). 
 mcp/tools.ts cypher edge list (agent-facing schema discovery). 
 isGraphWideRelType: INJECTS validity is a whole-program property — a 
change to a THIRD file (the interface, or a new/removed implementer) 
creates/invalidates edges between two untouched files (the TAINT_PATH / 
 #2084 M4 U6 class), so incremental extraction must always re-include the 
full fresh set. 
 deleteAllInjects (lbug-adapter): mirrors deleteAllInterprocTaintPaths — 
COUNT-then-DELETE under withConnLock, benign missing-table carve-out, 
re-throw otherwise (CodeRelation has no PK and there is no read-side 
dedup; a fail-soft delete + re-add would silently duplicate rows). 
 run-analyze.ts: the delete is UNCONDITIONAL, next to the Communities 
delete — deliberately NOT inside the options.pdg block: the di phase runs 
on every persisting analyze while the graph-wide re-include is 
unconditional, so a pdg-gated delete would append without deleting on 
every non-pdg incremental run (N runs = N copies). 
 local-backend.ts comment: opt-in traversal by design (not in default 
impact()/context() lists; no IMPACT_RELATION_CONFIDENCE entry per the 
WRAPS/FETCHES precedent — edges carry their own 0.8). 
 ARCHITECTURE.md: 14 -&gt; 15 phases, DAG diagram, phase table, skip-list. 
 
 Note: the tools.ts edge list also predates WRAPS/QUERIES/USES — that drift 
is pre-existing and left for a follow-up. 
 Idempotency pinned end-to-end: two successive incremental runs (real 
runFullAnalysis + real LadybugDB, unrelated-file touches) leave the INJECTS 
row count stable. 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 docs: describe INJECTS' actual precondition; drop stale fixed-at-16 comments (review 4616076037 P3) 
 
 The shared-schema doc for INJECTS claimed an @Autowired precondition the 
code (pre-fix) never checked, and hardwired Spring semantics into what is 
now a framework-neutral edge type. Reword: precondition is an injection 
annotation recognized by a per-language matcher in di-extractors/; 
framework specifics live in the reason payload, not the type contract. 
 security.test.ts comments still said the allow-list size 'stays fixed at 
16' (it is 17 and the assertion derives from EXPECTED_RELATION_TYPES). 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 refactor: simplify DI surfaces — narrow matcher contract, dedup delete-alls, derive tools edge list 
 
 Post-implementation simplification pass (4 review angles): 
 
 DiFieldMatch/CandidateField carried collectionType + matchedAnnotation 
that no consumer read (the matcher bakes both into reason) — narrowed to 
{elementTypeName, reason}. 
 parseElementTypeName had two guard branches fully subsumed by the final 
plain-dotted-type-name gate — deleted, rationale folded into the regex 
comment. 
 The three byte-identical delete-all-by-rel-type functions in lbug-adapter 
(TAINT_PATH / CALL_SUMMARY / INJECTS) are now one parameterized helper + 
thin wrappers with identical names, signatures, and message text 
(character-diff verified) — the missing-table regex and abort policy now 
live in exactly one place. 
 The cypher tool's hand-maintained edge-type list (already missing 
WRAPS/QUERIES/USES) is now derived from the canonical REL_TYPES — the 
drift class is gone rather than patched. 
 di phase: interface indexes are built only for languages that actually 
have candidates; test builder gained a rawDeclaredType opt-out replacing 
a hand-rolled node. 
 
 Co-Authored-By: Claude Fable 5 noreply@anthropic.com 
 
 fix: apply Tier-2 review findings — qualified-name fail-closed, honest cypher docs, pinned delete contract, hook isolation 
 
 
 byQualifiedName was last-writer-wins on duplicate qualified names 
(reproduced: order-dependent INJECTS edges with ambiguousSkipped 0 — 
same package+interface duplicated across monorepo modules/source roots; 
Java qualifiedName has no file-path component). Both indexes now share 
the AMBIGUOUS fail-closed sentinel; order-flip test added. 
 The REL_TYPES-derived cypher edge list advertised pdg-gated types with 
no caveat (LLM queries on them silently return zero rows on default 
indexes) — caveat appended, INJECTS example added, impact relationTypes 
description now names the DI fan-out opt-in. 
 The delete-all re-throw contract (only defense against duplicate 
CodeRelation rows) was untested — error classification extracted to a 
pure classifyDeleteAllError and pinned exhaustively. 
 extractRawType/extractAnnotations hooks lacked the per-hook try/catch 
the pipeline applies elsewhere ( #2286 pattern): a throw

[... truncated for safety ...]

</details>