---
id: inbox_feea732c
date: 2026-06-28
source_ref: "[[00-inbox/.../inbox_feea732c]]"
title: "Release Candidate v1.6.9-rc.26"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.26
source: gitnexus-releases
published_at: 2026-06-28T12:56:44+00:00
fetched_at: 2026-06-29T01:54:00.542265+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.9-rc.26 發布，包含對多種編程語言的代碼分析能力增強。新增 Python 和 Java 的源/匯點（source/sink）模型支持污點分析，涵蓋過程內與跨過程分析場景。Kotlin Spring HTTP 消費者提取現已達到與 Java 功能對等，並支持 Django 多倉庫路由提取。搜索功能改進使文檔注釋全文可檢索；TypeScript 作用域解析新增 Nuxt/Nitro 自動導入支持。修復包括 LadybugDB 雙重釋放崩潰、FastAPI APIRouter 前綴應用、Spring 方法級路由映射識別；性能優化則跳過已被圖覆蓋的路由文件的源解析。共計 21 項 PR 合併。"
key_points:
  - "Python/Java 污點分析模型支持跨過程與過程內分析，擴展代碼安全檢查範圍"
  - "Kotlin Spring HTTP 消費者提取與 Java 功能對等；支持多倉庫路由提取與 Nuxt/Nitro 自動導入"
  - "搜索索引改進（文檔注釋 FTS）與路由節點 (method, url) 標識符實現提升搜尋精度"
tags: [gitnexus, code-analysis, taint-analysis, polyglot-support]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.26

GitNexus v1.6.9-rc.26 發布，包含對多種編程語言的代碼分析能力增強。新增 Python 和 Java 的源/匯點（source/sink）模型支持污點分析，涵蓋過程內與跨過程分析場景。Kotlin Spring HTTP 消費者提取現已達到與 Java 功能對等，並支持 Django 多倉庫路由提取。搜索功能改進使文檔注釋全文可檢索；TypeScript 作用域解析新增 Nuxt/Nitro 自動導入支持。修復包括 LadybugDB 雙重釋放崩潰、FastAPI APIRouter 前綴應用、Spring 方法級路由映射識別；性能優化則跳過已被圖覆蓋的路由文件的源解析。共計 21 項 PR 合併。

### 重點
- Python/Java 污點分析模型支持跨過程與過程內分析，擴展代碼安全檢查範圍
- Kotlin Spring HTTP 消費者提取與 Java 功能對等；支持多倉庫路由提取與 Nuxt/Nitro 自動導入
- 搜索索引改進（文檔注釋 FTS）與路由節點 (method, url) 標識符實現提升搜尋精度

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.26)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.9-rc.26

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.26 \n Target base: 1.6.9 (rc #26 )\n Source commit (main): 7ca7166 \n Release commit (versioned tree): 84b7e65 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 @slugb0t made their first contribution in #2026 
 
 Full Changelog : v1.6.8...v1.6.9-rc.26

</details>