---
id: inbox_61b267ec
date: 2026-06-24
source_ref: "[[00-inbox/2026-06-24/2200-gitnexus-releases-release-candidate-v1-6-9-rc-15-63c5]]"
title: "Release Candidate v1.6.9-rc.15"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.15
source: gitnexus-releases
published_at: 2026-06-24T07:55:39+00:00
fetched_at: 2026-06-24T22:04:38.507271+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.9-rc.15 發布，變更清單與 rc.17、rc.16 相同，為同一版本開發週期內的迭代自動化構建。"
key_points:
  - "Python 及 Java source/sink 安全模型支援"
  - "跨倉庫 PDG 調用追踪、Django 多倉庫路由提取、Kotlin Spring HTTP 消費者提取功能"
tags: [gitnexus, code-analysis, release-candidate]
topics: []
importance: 1
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.15

GitNexus v1.6.9-rc.15 發布，變更清單與 rc.17、rc.16 相同，為同一版本開發週期內的迭代自動化構建。

### 重點
- Python 及 Java source/sink 安全模型支援
- 跨倉庫 PDG 調用追踪、Django 多倉庫路由提取、Kotlin Spring HTTP 消費者提取功能

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.15)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.15 \n Target base: 1.6.9 (rc #15 )\n Source commit (main): 8886d55 \n Release commit (versioned tree): 170ee86 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 
 Full Changelog : v1.6.8...v1.6.9-rc.15

</details>