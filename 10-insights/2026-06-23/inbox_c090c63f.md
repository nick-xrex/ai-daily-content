---
id: inbox_c090c63f
date: 2026-06-23
source_ref: "[[00-inbox/2026-06-23/2200-gitnexus-releases-release-candidate-v1-6-9-rc-12-bd40]]"
title: "Release Candidate v1.6.9-rc.12"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.12
source: gitnexus-releases
published_at: 2026-06-23T17:09:28+00:00
fetched_at: 2026-06-23T22:05:44.706526+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.9-rc.12 发布，为目标稳定版 1.6.9 的第 12 个 RC 版本。本版本新增 Python 污点分析 source/sink 模型、修复 Ladybug 数据库双重释放崩溃，修复 Kotlin fun interface 提取问题。支持 Kotlin Spring HTTP 消费者提取并与 Java 提供者功能对等、Django 多仓库路由提取、Java/Kotlin HTTP 消费者提取扩展、Java 保守型 source/sink 模型。性能方面跳过已覆盖文件的源码解析。新增 PDG 跨仓库调用追踪、跨文件命名 HTTP 处理程序解析、通过调用点行号解析内联 HTTP 提供者处理程序。新贡献者 @HuyNguyenDinh 首次参与。"
key_points:
  - "新增 Python 污点分析模型及 Java 保守型 source/sink 定义，扩大安全分析覆盖范围"
  - "Kotlin Spring HTTP 消费者提取与 Java 功能对等，支持 Django 多仓库路由提取"
  - "PDG 跨仓库调用追踪与 HTTP 处理程序多维度解析（命名、内联、行号对应），提升代码追踪精度"
tags: [code-analysis, release-candidate, taint-analysis, kotlin-spring, pdg]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.12

GitNexus v1.6.9-rc.12 发布，为目标稳定版 1.6.9 的第 12 个 RC 版本。本版本新增 Python 污点分析 source/sink 模型、修复 Ladybug 数据库双重释放崩溃，修复 Kotlin fun interface 提取问题。支持 Kotlin Spring HTTP 消费者提取并与 Java 提供者功能对等、Django 多仓库路由提取、Java/Kotlin HTTP 消费者提取扩展、Java 保守型 source/sink 模型。性能方面跳过已覆盖文件的源码解析。新增 PDG 跨仓库调用追踪、跨文件命名 HTTP 处理程序解析、通过调用点行号解析内联 HTTP 提供者处理程序。新贡献者 @HuyNguyenDinh 首次参与。

### 重點
- 新增 Python 污点分析模型及 Java 保守型 source/sink 定义，扩大安全分析覆盖范围
- Kotlin Spring HTTP 消费者提取与 Java 功能对等，支持 Django 多仓库路由提取
- PDG 跨仓库调用追踪与 HTTP 处理程序多维度解析（命名、内联、行号对应），提升代码追踪精度

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.12)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.12 \n Target base: 1.6.9 (rc #12 )\n Source commit (main): 698f5ef \n Release commit (versioned tree): 8e1aeee \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 
 Full Changelog : v1.6.8...v1.6.9-rc.12

</details>