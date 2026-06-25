---
id: inbox_a262497f
date: 2026-06-25
source_ref: "[[00-inbox/2026-06-25/2200-gitnexus-releases-release-candidate-v1-6-9-rc-18-4d2f]]"
title: "Release Candidate v1.6.9-rc.18"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.18
source: gitnexus-releases
published_at: 2026-06-25T00:33:55+00:00
fetched_at: 2026-06-25T22:05:02.674856+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.9-rc.18 RC 版本發布，包含多項代碼分析功能增強。新增 Python 和 Java 保守的 source/sink 模型、Kotlin Spring HTTP 消費者提取與提供者平價、Django 多倉庫路由提取、跨倉庫 PDG 調用追踪。性能優化方面跳過已圖覆蓋路由文件的源解析；支持 Spring 方法級數組形式路由映射、跨文件命名 HTTP handler 解析、內聯 provider 處理程序解析。文檔注釋現已在所有語言中可搜索，Nuxt/Nitro 自動導入 TypeScript 作用域解析亦獲支持。"
key_points:
  - "新增 Python 和 Java source/sink 模型，Kotlin Spring HTTP 提取達到與 Java 提供者平級，支持 Django 多倉庫路由提取"
  - "跨倉庫 PDG 調用追踤、Kotlin fun interface 支持、Nuxt/Nitro 自動導入 TypeScript 作用域解析"
  - "性能最適化：跳過已圖覆蓋路由文件源解析；文檔注釋全語言可搜索；Spring 方法級數組路由映射識別"
tags: [gitnexus, code-analysis, static-analysis, multi-language-support]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.18

GitNexus v1.6.9-rc.18 RC 版本發布，包含多項代碼分析功能增強。新增 Python 和 Java 保守的 source/sink 模型、Kotlin Spring HTTP 消費者提取與提供者平價、Django 多倉庫路由提取、跨倉庫 PDG 調用追踪。性能優化方面跳過已圖覆蓋路由文件的源解析；支持 Spring 方法級數組形式路由映射、跨文件命名 HTTP handler 解析、內聯 provider 處理程序解析。文檔注釋現已在所有語言中可搜索，Nuxt/Nitro 自動導入 TypeScript 作用域解析亦獲支持。

### 重點
- 新增 Python 和 Java source/sink 模型，Kotlin Spring HTTP 提取達到與 Java 提供者平級，支持 Django 多倉庫路由提取
- 跨倉庫 PDG 調用追踤、Kotlin fun interface 支持、Nuxt/Nitro 自動導入 TypeScript 作用域解析
- 性能最適化：跳過已圖覆蓋路由文件源解析；文檔注釋全語言可搜索；Spring 方法級數組路由映射識別

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.18)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.18 \n Target base: 1.6.9 (rc #18 )\n Source commit (main): ba071b5 \n Release commit (versioned tree): 1f5e267 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 Full Changelog : v1.6.8...v1.6.9-rc.18

</details>