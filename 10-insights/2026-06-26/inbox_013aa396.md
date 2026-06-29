---
id: inbox_013aa396
date: 2026-06-26
source_ref: "[[00-inbox/.../inbox_013aa396]]"
title: "Release Candidate v1.6.9-rc.25"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.25
source: gitnexus-releases
published_at: 2026-06-26T19:09:37+00:00
fetched_at: 2026-06-29T00:53:59.590495+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.9-rc.25 發布，累積自 v1.6.8 以來多項重要功能和修復。新增 Python 和保守式 Java source/sink 模型用於污點分析。修復 LadybugDB double-free 崩潰並強化連線序列化。Kotlin Spring HTTP consumer extraction 功能達到 Java 對等程度。新增 Django multi-repo route extraction、cross-repo PDG 呼叫追蹤、Nuxt/Nitro auto-imports 解析。改進文檔註釋搜尋、Route node identity、Spring interface-inherited routes 和內聯 HTTP handler 解析。"
key_points:
  - "Python 和保守式 Java source/sink 模型用於污點分析（taint analysis）（#2253、#2267）"
  - "LadybugDB double-free 崩潰修復與連線序列化強化（#2264）"
  - "Django multi-repo route extraction、cross-repo PDG 追蹤（#2269）、Nuxt/Nitro auto-imports 支援（#2026）"
tags: [gitnexus, taint-analysis, http-extraction, code-graph, release-candidate]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.25

GitNexus v1.6.9-rc.25 發布，累積自 v1.6.8 以來多項重要功能和修復。新增 Python 和保守式 Java source/sink 模型用於污點分析。修復 LadybugDB double-free 崩潰並強化連線序列化。Kotlin Spring HTTP consumer extraction 功能達到 Java 對等程度。新增 Django multi-repo route extraction、cross-repo PDG 呼叫追蹤、Nuxt/Nitro auto-imports 解析。改進文檔註釋搜尋、Route node identity、Spring interface-inherited routes 和內聯 HTTP handler 解析。

### 重點
- Python 和保守式 Java source/sink 模型用於污點分析（taint analysis）（#2253、#2267）
- LadybugDB double-free 崩潰修復與連線序列化強化（#2264）
- Django multi-repo route extraction、cross-repo PDG 追蹤（#2269）、Nuxt/Nitro auto-imports 支援（#2026）

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.25)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.9-rc.25

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.25 \n Target base: 1.6.9 (rc #25 )\n Source commit (main): 57e4afa \n Release commit (versioned tree): b653128 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 @slugb0t made their first contribution in #2026 
 
 Full Changelog : v1.6.8...v1.6.9-rc.25

</details>