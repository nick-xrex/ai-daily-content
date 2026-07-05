---
id: inbox_f7ee558b
date: 2026-07-04
source_ref: "[[00-inbox/.../inbox_f7ee558b]]"
title: "v1.6.9"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9
source: gitnexus-releases
published_at: 2026-07-04T07:14:39+00:00
fetched_at: 2026-07-05T01:42:20.746526+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.9 穩定版發布，主題為「多倉庫 API 追蹤發布」（the multi-repo API-tracing release）。核心新功能是在 PDG 基礎上實現跨倉庫最短路徑呼叫追蹤，能追蹤跨越不同倉庫的 ContractLink 呼叫鏈路。HTTP 路由與消費者提取功能大幅擴展：新增 Kotlin Spring 與 Java 功能對等的消費者提取、Django 多倉庫路由支援、FastAPI APIRouter 建構子字首應用、Spring 介面繼承路由解析。污點分析引擎得到補完，新增 Java 和 Python 的保守式源/匯模型，搭配既有的跨函式污點引擎形成完整分析鏈。工作空間索引改為動態跟隨當前檢出分支而非固定在建立時分支，搜尋功能新增 opt-in CJK 分詞分割、可配置 FTS 詞幹與向量距離閾值。版本包含 50+ 項修復與改進。"
key_points:
  - "跨倉庫 PDG 呼叫追蹤：支援追蹤 ContractLink 跨越不同倉庫的最短呼叫路徑；HTTP 路由提取新增 Kotlin Spring consumer、Django、FastAPI 支援"
  - "污點分析補完：新增 Java 和 Python 保守式源/匯模型，搭配跨函式污點引擎實現完整分析鏈；污點模型適用於安全性分析"
  - "工作空間索引動態化 + 搜尋改進：索引跟隨 git checkout；opt-in CJK 分詞分割、可配置 FTS 詞幹、向量距離閾值；Route 節點以 (method, url) 區分"
tags: [gitnexus, cross-repo-analysis, api-tracing, taint-analysis, pdg]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v1.6.9

GitNexus v1.6.9 穩定版發布，主題為「多倉庫 API 追蹤發布」（the multi-repo API-tracing release）。核心新功能是在 PDG 基礎上實現跨倉庫最短路徑呼叫追蹤，能追蹤跨越不同倉庫的 ContractLink 呼叫鏈路。HTTP 路由與消費者提取功能大幅擴展：新增 Kotlin Spring 與 Java 功能對等的消費者提取、Django 多倉庫路由支援、FastAPI APIRouter 建構子字首應用、Spring 介面繼承路由解析。污點分析引擎得到補完，新增 Java 和 Python 的保守式源/匯模型，搭配既有的跨函式污點引擎形成完整分析鏈。工作空間索引改為動態跟隨當前檢出分支而非固定在建立時分支，搜尋功能新增 opt-in CJK 分詞分割、可配置 FTS 詞幹與向量距離閾值。版本包含 50+ 項修復與改進。

### 重點
- 跨倉庫 PDG 呼叫追蹤：支援追蹤 ContractLink 跨越不同倉庫的最短呼叫路徑；HTTP 路由提取新增 Kotlin Spring consumer、Django、FastAPI 支援
- 污點分析補完：新增 Java 和 Python 保守式源/匯模型，搭配跨函式污點引擎實現完整分析鏈；污點模型適用於安全性分析
- 工作空間索引動態化 + 搜尋改進：索引跟隨 git checkout；opt-in CJK 分詞分割、可配置 FTS 詞幹、向量距離閾值；Route 節點以 (method, url) 區分

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v1.6.9

GitNexus v1.6.9 
 
 The multi-repo API-tracing release. group now resolves HTTP routes and consumers across files, frameworks, and repos — including a cross-repo call trace over the PDG — while the default workspace index quietly follows whatever branch you have checked out, and taint modeling rounds out Java and Python. 
 
 ✨ Highlights 
 
 🌐 Cross-repo call trace over the PDG — group can trace the shortest call path across a ContractLink between two repositories, not just within one. ( #2269 ) 
 🔗 HTTP handler resolution goes cross-file and inline for group — named handlers defined in another file, and inline provider handlers resolved by call-site line. ( #2275 , #2277 , #2276 , #2282 ) 
 🍃 HTTP route/consumer extraction rounded out — Java and Kotlin HTTP consumer extraction expanded with Kotlin Spring provider parity, Django route extraction for multi-repo group , and a Spring DI resolver for @Autowired List&lt;T&gt; injection. ( #2268 , #2254 , #1836 , #2200 ) 
 🌱 Taint source/sink models added for Java and Python , alongside the intra/inter-procedural taint engine shipped in 1.6.8. ( #2267 , #2253 ) 
 🌿 The default (non-multi-branch) workspace index now follows the checked-out branch instead of staying pinned to whichever branch it was created on. ( #2364 ) 
 🔍 Search gets sharper — opt-in CJK bigram segmentation for FTS, a configurable FTS stemmer and vector distance threshold, and more compact, description-forward embedding text. ( #2339 , #2307 , #2330 , #2333 , #2334 ) 
 
 
 🚀 Added 
 
 Flat workspace index follows the checked-out branch — the default (non-multi-branch) index now tracks git checkout instead of staying pinned to the branch it was created on ( #2364 ) 
 Spring DI resolver for @Autowired List&lt;T&gt; injection — collection-typed constructor/field injection resolves to all matching bean implementations ( #2200 ) 
 Opt-in CJK bigram segmentation for FTS search — improves search relevance over Chinese/Japanese/Korean text ( #2339 ) 
 Compact, description-forward embedding text — shorter, more targeted embedding input for symbol search ( #2333 , #2334 ) 
 Route nodes get a (method, url) identity — distinct HTTP verbs on the same URL are no longer merged into one node ( #2289 , #2302 ) 
 Nuxt/Nitro auto-imports resolved in the TypeScript scope resolver ( #2026 ) 
 Doc comments searchable across all languages via FTS ( #2286 ) 
 Cross-file and inline HTTP handler resolution for group — named handlers across files ( #2275 , #2277 ) and inline provider handlers via call-site line ( #2276 , #2282 ) 
 Cross-repo call trace using PDG for group ( #2269 ) 
 Java and Python conservative taint source/sink models ( #2267 , #2253 ) 
 Java and Kotlin HTTP consumer extraction expanded , with Kotlin Spring provider parity ( #2268 , #2254 , #1888 ) 
 Django route extraction for multi-repo group ( #1836 ) 
 Kilo Code + GitNexus MCP setup guide ( #2259 ) 
 
 🐛 Fixed 
 
 Index metadata renamed to gitnexus.json with dual-write compatibility for existing indexes ( #2363 ) 
 Java call graph — cast-wrapped and this.method() receivers now resolve call edges ( #2357 ) 
 Icon imports consolidated — fixes stale refs and a package-name collision ( #2343 ) 
 Embeddings — CUDA 13 hosts now use a system-matched onnxruntime-node build for GPU acceleration ( #2341 ) 
 Ladybug single-writer transaction contention now retries instead of failing ( #2342 ) 
 --limit CLI flag — i18n-safe, guards 0/negative values, and truncates at the correct path ( #2310 ) 
 Ladybug pinned to 0.18.0 , validating the multi-writer deadlock fix ( #2340 ) 
 Full text file content stays searchable in the FTS index ( #2323 ) 
 Vector distance threshold made configurable ( #2330 ) 
 LadybugDB-incompatible multi-label Cypher replaced in group queries ( #2325 , #2327 ) 
 Windows @group reopen — read-only bridge handle is cached to fix repeated reopen failures ( #2274 , #2313 ) 
 FTS stemmer made configurable ( #2307 ) 
 FastAPI APIRouter constructor prefixes applied to nested routes ( #2312 ) 
 MCP api_impact response shape stabilized for same-URL multi-verb routes ( #2308 , #2309 ) 
 Generator function declarations indexed ( #2305 ) 
 FTS indexes the description field so doc comments are keyword-searchable ( #2300 ) 
 Spring interface-inherited routes resolved ( #2288 , #2290 ) 
 Spring method-level array-form route mappings recognized ( #2281 ) 
 MCP impact callgraph mode tolerates adapter-materialized line:0 ( #2279 , #2283 ) 
 Kotlin fun interface extraction via a tree-sitter-kotlin re-vendor ( #2271 ) 
 --pdg analyze double-free fixed — LadybugDB close-destructor crash avoided and connection serialization hardened ( #2264 ) 
 
 🔧 Changed 
 
 Root README restructured and all READMEs fact-checked ( #2360 ) 
 Bundled skill reference drift fixed in docs ( #2362 ) 
 
 ⚡ Performance 
 
 group /HTTP route extraction skips source parsing for files already covered by the graph ( #2138 Part 2, #2265 ) 
 
 
 📦 Chore / Dependencies — 20 dependency &amp; CI-action bumps
 
 gitnexus runtime — node-addon-api 8.8.0 → 8.9.0 ( #2366 ), commander 14.0.3 → 15.0.0 ( #2322 ), onnxruntime-node ( #2321 ), onnxruntime-common ( #2320 ), uuid 14.0.0 → 14.0.1 ( #2285 ) 
 gitnexus dev — @types/node ( #2273 ) 
 gitnexus-web — lucide-react ( #2349 ), @langchain/langgraph ( #2344 ), @playwright/test ( #2346 ), @langchain/openai ( #2348 , #2291 ), @langchain/google-genai ( #2345 ), langchain 1.4.4 → 1.4.6 ( #2294 ), @vitest/coverage-v8 ( #2297 ), lru-cache 11.3.6 → 11.5.1 ( #2298 ), @langchain/core ( #2293 ) 
 CI actions — softprops/action-gh-release 3.0.0 → 3.0.1 ( #2352 ), actions/cache 5.0.5 → 6.1.0 ( #2351 ), actions/setup-python 6.2.0 → 6.3.0 ( #2350 ), actions/checkout 6.0.3 → 7.0.0 ( #2292 ), release-drafter/release-drafter 7.3.1 → 7.4.0 ( #2295 ) 
 
 
 
 📥 Upgrade 
 npm install -g gitnexus@1.6.9 
 Then re-index to pick up the workspace-index and Route-identity changes: 
 gitnexus analyze 
 Full changelog: v1.6.8...v1.6.9

</details>