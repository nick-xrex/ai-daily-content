---
id: inbox_e43720d4
date: 2026-06-25
source_ref: "[[00-inbox/2026-06-25/2200-gitnexus-releases-release-candidate-v1-6-9-rc-19-b8a8]]"
title: "Release Candidate v1.6.9-rc.19"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.19
source: gitnexus-releases
published_at: 2026-06-25T05:44:28+00:00
fetched_at: 2026-06-25T22:04:06.127226+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 发布 v1.6.9-rc.19（rc #19 / npm: gitnexus@rc），发布候选版本用于早期测试。改进包括：Python 和 Java source/sink 安全模型；Kotlin Spring HTTP 消费者提取与 Java 奇偶校验；Django 多仓库路由提取；Java 和 Kotlin HTTP 消费者提取扩展；跨仓库调用链追踪（PDG）；全语言文档注释可搜索；性能优化。修复 LadybugDB 双重释放和连接序列化问题；Spring 方法级数组形式路由映射识别。相比 rc.20，部分提交新增或优化。"
key_points:
  - "Python 和 Java source/sink 安全模型支持，扩展 taint 分析覆盖范围"
  - "Kotlin Spring 提取与 Java 提供者奇偶校验、Django 多仓库路由、跨仓库调用追踪"
  - "全语言文档注释可搜索；性能优化；LadybugDB 序列化和双重释放修复"
tags: [gitnexus, code-analysis, taint-tracking, multi-language]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.19

GitNexus 发布 v1.6.9-rc.19（rc #19 / npm: gitnexus@rc），发布候选版本用于早期测试。改进包括：Python 和 Java source/sink 安全模型；Kotlin Spring HTTP 消费者提取与 Java 奇偶校验；Django 多仓库路由提取；Java 和 Kotlin HTTP 消费者提取扩展；跨仓库调用链追踪（PDG）；全语言文档注释可搜索；性能优化。修复 LadybugDB 双重释放和连接序列化问题；Spring 方法级数组形式路由映射识别。相比 rc.20，部分提交新增或优化。

### 重點
- Python 和 Java source/sink 安全模型支持，扩展 taint 分析覆盖范围
- Kotlin Spring 提取与 Java 提供者奇偶校验、Django 多仓库路由、跨仓库调用追踪
- 全语言文档注释可搜索；性能优化；LadybugDB 序列化和双重释放修复

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.19)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.19 \n Target base: 1.6.9 (rc #19 )\n Source commit (main): a05a165 \n Release commit (versioned tree): 2286732 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 Full Changelog : v1.6.8...v1.6.9-rc.19

</details>