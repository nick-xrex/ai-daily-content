---
id: inbox_e778913e
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.45"
author: "github-actions[bot]"
published_at: 2026-07-03T18:51:26+00:00
fetched_at: 2026-07-04T01:15:47.906273+00:00
content_hash: "f8bcd3cfa89baeb891da6c192d965be13eeb223a04a85a105de69260133e9a02"
lang: en
caption_quality: None
raw: true
topics: []
---

# Release Candidate v1.6.9-rc.45

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.45 \n Target base: 1.6.9 (rc #45 )\n Source commit (main): d546fa3 \n Release commit (versioned tree): bd459b7 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 @slugb0t made their first contribution in #2026 
 @S23Web3 made their first contribution in #2310 
 @ACT900 made their first contribution in #2341 
 @fix2015 made their first contribution in #2343 
 @oktanishq made their first contribution in #2259 
 @LivioGama made their first contribution in #2363 
 
 Full Changelog : v1.6.8...v1.6.9-rc.45