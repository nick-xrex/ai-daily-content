---
id: inbox_defdad39
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-gitnexus-releases-release-candidate-v1-6-9-rc-46-8823]]"
title: "Release Candidate v1.6.9-rc.46"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.46
source: gitnexus-releases
published_at: 2026-07-03T20:14:06+00:00
fetched_at: 2026-07-04T01:20:23.359614+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.9-rc.46 為代碼分析引擎帶來大量功能增強。新增 Python 和 Java 保守型 source/sink 模型，支持污點分析（taint analysis）。Kotlin Spring HTTP 消費者提取功能達到與 Java 功能對等，新增 Django 多倉庫路由提取和跨倉庫 PDG 調用追蹤。搜索功能改進包括 CJK 分詞支持、FTS 詞幹算法配置、文檔注釋全文索引、向量距離閾值可配。嵌入和性能優化包括緊湊嵌入文本表示、ONNX GPU 加速（CUDA 13 支持）、LadybugDB 死鎖修復。"
key_points:
  - "新增 Python 和 Java source/sink 模型，支持跨多語言的污點分析"
  - "Kotlin Spring + Django 多倉庫支持、跨倉庫 PDG 調用追蹤，支持 Nuxt/Nitro auto-import 解析"
  - "搜索和性能優化：CJK 分詞、FTS 文檔搜索、ONNX GPU 加速（CUDA 13）、LadybugDB 死鎖修復"
tags: [gitnexus, code-analysis, taint-analysis, multi-repo]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.46

GitNexus v1.6.9-rc.46 為代碼分析引擎帶來大量功能增強。新增 Python 和 Java 保守型 source/sink 模型，支持污點分析（taint analysis）。Kotlin Spring HTTP 消費者提取功能達到與 Java 功能對等，新增 Django 多倉庫路由提取和跨倉庫 PDG 調用追蹤。搜索功能改進包括 CJK 分詞支持、FTS 詞幹算法配置、文檔注釋全文索引、向量距離閾值可配。嵌入和性能優化包括緊湊嵌入文本表示、ONNX GPU 加速（CUDA 13 支持）、LadybugDB 死鎖修復。

### 重點
- 新增 Python 和 Java source/sink 模型，支持跨多語言的污點分析
- Kotlin Spring + Django 多倉庫支持、跨倉庫 PDG 調用追蹤，支持 Nuxt/Nitro auto-import 解析
- 搜索和性能優化：CJK 分詞、FTS 文檔搜索、ONNX GPU 加速（CUDA 13）、LadybugDB 死鎖修復

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.46)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.46 \n Target base: 1.6.9 (rc #46 )\n Source commit (main): e46b87f \n Release commit (versioned tree): 633c33b \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(taint): add Python source/sink model by @azizur100389 in #2253 
 fix(lbug): stop --pdg analyze double-free (skip LadybugDB close-destructor crash) + harden connection serialization by @magyargergo in #2264 
 feat(group): Kotlin Spring HTTP consumer extraction + provider parity with Java by @glier in #2254 
 feat(group): Support Django route extraction for multi-repo by @HuyNguyenDinh in #1836 
 feat(group): expand Java and Kotlin HTTP consumer extraction (re #1888 ) by @magyargergo in #2268 
 feat(taint): add conservative Java source/sink model by @azizur100389 in #2267 
 perf(group/http): skip source parse for graph-covered route files ( #2138 Part 2) by @henry201605 in #2265 
 feat(group): cross-repo call trace using PDG by @magyargergo in #2269 
 fix(lang-kotlin): support fun interface extraction via tree-sitter-kotlin re-vendor by @glier in #2271 
 feat(group): resolve cross-file named HTTP handlers ( #2275 ) by @magyargergo in #2277 
 feat(group): resolve inline HTTP provider handlers via call-site line ( #2276 ) by @magyargergo in #2282 
 fix(mcp): tolerate adapter-materialized line:0 in impact callgraph mode ( #2279 ) by @magyargergo in #2283 
 fix(ingestion/routes): recognise Spring method-level array-form route mappings by @henry201605 in #2281 
 feat(ingestion): make doc comments searchable across all languages by @magyargergo in #2286 
 feat: ✨ resolve Nuxt/Nitro auto-imports in TypeScript scope resolver by @slugb0t in #2026 
 fix(ingestion/routes): resolve Spring interface-inherited routes ( #2288 ) by @henry201605 in #2290 
 fix(search): index description field for FTS so doc comments are keyword-searchable by @magyargergo in #2300 
 feat(ingestion/routes): give Route nodes a (method, url) identity ( #2289 ) by @henry201605 in #2302 
 fix(ingestion): index generator function declarations by @koriyoshi2041 in #2305 
 fix(mcp): stabilize api_impact response shape for same-URL multi-verb routes ( #2308 ) by @magyargergo in #2309 
 fix(fastapi): apply APIRouter constructor prefixes by @koriyoshi2041 in #2312 
 fix(search): make FTS stemmer configurable by @koriyoshi2041 in #2307 
 fix(test): stabilize local Windows gate baselines by @azizur100389 in #2314 
 fix(group): cache read-only bridge handle to fix Windows @group reopen ( #2274 ) by @prajapatisparsh in #2313 
 fix(group): replace LadybugDB-incompatible multi-label Cypher ( #2325 ) by @magyargergo in #2327 
 fix(search): make vector distance threshold configurable by @koriyoshi2041 in #2330 
 feat(embeddings): compact, description-forward embedding text ( #2333 ) by @magyargergo in #2334 
 fix(indexing): keep full text file content searchable by @koriyoshi2041 in #2323 
 feat(search): add opt-in CJK bigram segmentation for FTS search by @magyargergo in #2339 
 fix(deps): pin Ladybug 0.18.0, validate the multi-writer deadlock fix by @magyargergo in #2340 
 fix(cli): --limit i18n, 0/negative guard, and correct truncation paths by @S23Web3 in #2310 
 fix(lbug): retry single-writer transaction contention by @koriyoshi2041 in #2342 
 fix(embeddings): use system-matched onnxruntime-node CUDA build so CUDA 13 hosts use the GPU by @ACT900 in #2341 
 fix: consolidate icon imports, fix stale refs and package name collision by @fix2015 in #2343 
 Add Kilo Code + GitNexus MCP setup guide by @oktanishq in #2259 
 fix: Java cast-wrapped and this.method() call edges by @magyargergo in #2357 
 feat: add Spring DI resolver for @Autowired List injection by @ChunxueLi in #2200 
 docs: restructure root README, fact-check all READMEs by @magyargergo in #2360 
 docs: fix bundled skill reference drift by @koriyoshi2041 in #2362 
 fix(storage): rename index metadata to gitnexus.json with dual-write compatibility by @LivioGama in #2363 
 feat: flat workspace index follows the checked-out branch by @magyargergo in #2364 
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 @slugb0t made their first contribution in #2026 
 @S23Web3 made their first contribution in #2310 
 @ACT900 made their first contribution in #2341 
 @fix2015 made their first contribution in #2343 
 @oktanishq made their first contribution in #2259 
 @LivioGama made their first contribution in #2363 
 
 Full Changelog : v1.6.8...v1.6.9-rc.46

</details>