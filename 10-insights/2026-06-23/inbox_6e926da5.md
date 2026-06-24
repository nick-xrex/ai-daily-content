---
id: inbox_6e926da5
date: 2026-06-23
source_ref: "[[00-inbox/2026-06-23/2200-gitnexus-releases-release-candidate-v1-6-9-rc-11-58da]]"
title: "Release Candidate v1.6.9-rc.11"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.11
source: gitnexus-releases
published_at: 2026-06-23T11:31:50+00:00
fetched_at: 2026-06-23T22:05:44.715864+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.9-rc.11 发布，为目标稳定版 1.6.9 的第 11 个 RC 版本。相比 rc.12 缺少「通过调用点行号解析内联 HTTP 提供者处理程序」的特性，其他变更与 rc.12 一致：新增 Python 污点分析模型、修复 Ladybug 双重释放崩溃、支持 Kotlin Spring HTTP 消费者提取、Django 多仓库路由提取、扩展 Java/Kotlin HTTP 消费者提取、新增 Java source/sink 模型、优化性能、支持 PDG 跨仓库调用追踪、修复 Kotlin fun interface 提取、支持跨文件命名 HTTP 处理程序解析。新贡献者首次参与。"
key_points:
  - "与 rc.12 基本特性集相同，缺少内联 HTTP 提供者处理程序的行号对应解析"
  - "Kotlin Spring HTTP 消费者提取与 Java 功能对等，支持 Django 多仓库场景"
  - "PDG 跨仓库调用追踪与跨文件 HTTP 处理程序解析"
tags: [code-analysis, release-candidate, taint-analysis, kotlin-spring]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.11

GitNexus v1.6.9-rc.11 发布，为目标稳定版 1.6.9 的第 11 个 RC 版本。相比 rc.12 缺少「通过调用点行号解析内联 HTTP 提供者处理程序」的特性，其他变更与 rc.12 一致：新增 Python 污点分析模型、修复 Ladybug 双重释放崩溃、支持 Kotlin Spring HTTP 消费者提取、Django 多仓库路由提取、扩展 Java/Kotlin HTTP 消费者提取、新增 Java source/sink 模型、优化性能、支持 PDG 跨仓库调用追踪、修复 Kotlin fun interface 提取、支持跨文件命名 HTTP 处理程序解析。新贡献者首次参与。

### 重點
- 与 rc.12 基本特性集相同，缺少内联 HTTP 提供者处理程序的行号对应解析
- Kotlin Spring HTTP 消费者提取与 Java 功能对等，支持 Django 多仓库场景
- PDG 跨仓库调用追踪与跨文件 HTTP 处理程序解析

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.11)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.11 \n Target base: 1.6.9 (rc #11 )\n Source commit (main): 49ffd8e \n Release commit (versioned tree): 3a72964 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 
 Full Changelog : v1.6.8...v1.6.9-rc.11

</details>