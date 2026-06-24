---
id: inbox_f3b0ef4b
date: 2026-06-24
source_ref: "[[00-inbox/2026-06-24/2200-gitnexus-releases-release-candidate-v1-6-9-rc-14-437a]]"
title: "Release Candidate v1.6.9-rc.14"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.14
source: gitnexus-releases
published_at: 2026-06-24T06:29:01+00:00
fetched_at: 2026-06-24T22:06:40.739284+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.9-rc.14 版本發布 RC 構建。新增 Python 和保守 Java source/sink 污點分析模型，強化代碼安全檢測。修復 Ladybug 中的 double-free crash 問題，並改進連接序列化以提升穩定性。擴展多框架支持：Kotlin Spring 的 HTTP consumer 提取、Java HTTP consumer 擴展、Django 多倉庫路由提取、Nuxt/Nitro 自動導入解析。新增 PDG-based 跨倉庫調用追蹤功能，實現跨文件命名 HTTP handlers 和 inline HTTP provider handlers 解析。優化性能：跳過已圖覆蓋的路由文件源碼解析，改進 Spring method-level array-form 路由映射識別。"
key_points:
  - "新增 Python/Java source-sink 污點分析模型，提升代碼安全檢測能力"
  - "擴展框架支持：Kotlin Spring HTTP consumer、Django 多倉庫路由、Nuxt/Nitro 自動導入"
  - "PDG-based 跨倉庫呼叫追蹤與 Spring method-level array-form 路由映射識別"
tags: [code-analysis, security-analysis, framework-support, performance-optimization, multi-language]
topics: []
importance: 4
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.14

GitNexus v1.6.9-rc.14 版本發布 RC 構建。新增 Python 和保守 Java source/sink 污點分析模型，強化代碼安全檢測。修復 Ladybug 中的 double-free crash 問題，並改進連接序列化以提升穩定性。擴展多框架支持：Kotlin Spring 的 HTTP consumer 提取、Java HTTP consumer 擴展、Django 多倉庫路由提取、Nuxt/Nitro 自動導入解析。新增 PDG-based 跨倉庫調用追蹤功能，實現跨文件命名 HTTP handlers 和 inline HTTP provider handlers 解析。優化性能：跳過已圖覆蓋的路由文件源碼解析，改進 Spring method-level array-form 路由映射識別。

### 重點
- 新增 Python/Java source-sink 污點分析模型，提升代碼安全檢測能力
- 擴展框架支持：Kotlin Spring HTTP consumer、Django 多倉庫路由、Nuxt/Nitro 自動導入
- PDG-based 跨倉庫呼叫追蹤與 Spring method-level array-form 路由映射識別

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.14)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.14 \n Target base: 1.6.9 (rc #14 )\n Source commit (main): 0936553 \n Release commit (versioned tree): 406b069 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 
 Full Changelog : v1.6.8...v1.6.9-rc.14

</details>