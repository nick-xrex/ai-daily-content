---
id: inbox_ecdc79c3
date: 2026-06-29
source_ref: "[[00-inbox/2026-06-29/2218-gitnexus-releases-release-candidate-v1-6-9-rc-27-91e6]]"
title: "Release Candidate v1.6.9-rc.27"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.27
source: gitnexus-releases
published_at: 2026-06-29T04:32:59+00:00
fetched_at: 2026-06-29T23:11:04.502828+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 發布版本 1.6.9-rc.27。本次更新在多個程式語言的靜態分析能力上有所擴展：新增 Python 污點分析模型、保守型 Java 污點分析，強化 Kotlin Spring HTTP 消費者/提供者提取，支援跨倉庫 Django 路由提取。修復 LadybugDB 雙釋放崩潰與線程安全問題。另外實現跨檔案 HTTP 處理程式解析、FTS 全文搜尋優化（doc 註釋索引化、Stemmer 可配置化）、Nuxt/Nitro 自動導入型態解析等功能。"
key_points:
  - "GitNexus v1.6.9-rc.27：Python/Java 污點分析、Kotlin/Java HTTP 消費者提取增強、Django 跨倉庫路由支援"
  - "修復 LadybugDB 雙釋放崩潰、線程安全問題、API 影響響應穩定化"
  - "FTS 搜尋優化、doc 註釋可搜尋、Nuxt/Nitro 型態解析改進"
tags: [gitnexus, code-analysis, java-taint, kotlin-spring, django]
topics: []
importance: 3
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.27

GitNexus 發布版本 1.6.9-rc.27。本次更新在多個程式語言的靜態分析能力上有所擴展：新增 Python 污點分析模型、保守型 Java 污點分析，強化 Kotlin Spring HTTP 消費者/提供者提取，支援跨倉庫 Django 路由提取。修復 LadybugDB 雙釋放崩潰與線程安全問題。另外實現跨檔案 HTTP 處理程式解析、FTS 全文搜尋優化（doc 註釋索引化、Stemmer 可配置化）、Nuxt/Nitro 自動導入型態解析等功能。

### 重點
- GitNexus v1.6.9-rc.27：Python/Java 污點分析、Kotlin/Java HTTP 消費者提取增強、Django 跨倉庫路由支援
- 修復 LadybugDB 雙釋放崩潰、線程安全問題、API 影響響應穩定化
- FTS 搜尋優化、doc 註釋可搜尋、Nuxt/Nitro 型態解析改進

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.27)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.27 \n Target base: 1.6.9 (rc #27 )\n Source commit (main): a7df8f8 \n Release commit (versioned tree): daf43ad \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 @slugb0t made their first contribution in #2026 
 
 Full Changelog : v1.6.8...v1.6.9-rc.27

</details>