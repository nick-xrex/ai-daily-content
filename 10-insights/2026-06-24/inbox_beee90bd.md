---
id: inbox_beee90bd
date: 2026-06-24
source_ref: "[[00-inbox/2026-06-24/2200-gitnexus-releases-release-candidate-v1-6-9-rc-17-0cda]]"
title: "Release Candidate v1.6.9-rc.17"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.17
source: gitnexus-releases
published_at: 2026-06-24T21:33:52+00:00
fetched_at: 2026-06-24T22:04:38.501845+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 發布 v1.6.9-rc.17，進一步擴展多語言代碼分析能力與安全模型。新增 Python 和保守型 Java 的 source/sink 污點分析模型。支援 Kotlin Spring HTTP 消費者提取與 Java 功能對等，新增 Django 多倉庫路由提取與跨倉庫 PDG 調用追踪。改進 LadybugDB 雙重釋放問題，支援 Spring 方法級陣列形式路由映射識別，及 Nuxt/Nitro 自動導入的 TypeScript 作用域解析。性能優化對已圖覆蓋的路由文件跳過原始碼解析。"
key_points:
  - "新增 Python source/sink 模型及保守型 Java source/sink 模型用於污點分析"
  - "跨倉庫 PDG 調用追踪、Django 多倉庫路由提取、Kotlin Spring HTTP 消費者提取 + Java 功能對等"
  - "LadybugDB 連接序列化加強、Spring 方法級陣列路由映射支援、Nuxt/Nitro TypeScript 自動導入解析"
tags: [gitnexus, code-analysis, security-modeling, multi-repo-tracking, language-support]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.17

GitNexus 發布 v1.6.9-rc.17，進一步擴展多語言代碼分析能力與安全模型。新增 Python 和保守型 Java 的 source/sink 污點分析模型。支援 Kotlin Spring HTTP 消費者提取與 Java 功能對等，新增 Django 多倉庫路由提取與跨倉庫 PDG 調用追踪。改進 LadybugDB 雙重釋放問題，支援 Spring 方法級陣列形式路由映射識別，及 Nuxt/Nitro 自動導入的 TypeScript 作用域解析。性能優化對已圖覆蓋的路由文件跳過原始碼解析。

### 重點
- 新增 Python source/sink 模型及保守型 Java source/sink 模型用於污點分析
- 跨倉庫 PDG 調用追踪、Django 多倉庫路由提取、Kotlin Spring HTTP 消費者提取 + Java 功能對等
- LadybugDB 連接序列化加強、Spring 方法級陣列路由映射支援、Nuxt/Nitro TypeScript 自動導入解析

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.17)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.17 \n Target base: 1.6.9 (rc #17 )\n Source commit (main): 5165686 \n Release commit (versioned tree): 247a891 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 @slugb0t made their first contribution in #2026 
 
 Full Changelog : v1.6.8...v1.6.9-rc.17

</details>