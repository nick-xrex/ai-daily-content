---
id: inbox_f98d4669
date: 2026-06-23
source_ref: "[[00-inbox/2026-06-23/2200-gitnexus-releases-release-candidate-v1-6-9-rc-10-4090]]"
title: "Release Candidate v1.6.9-rc.10"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.10
source: gitnexus-releases
published_at: 2026-06-23T09:19:42+00:00
fetched_at: 2026-06-23T22:05:44.717609+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.9-rc.10 发布，为目标稳定版 1.6.9 的第 10 个 RC 版本。相比 rc.12 缺少「通过调用点行号解析内联 HTTP 提供者处理程序」与「跨文件命名 HTTP 处理程序解析」两项特性。包含 Python 污点分析模型、修复 Ladybug 双重释放崩溃、Kotlin Spring HTTP 消费者提取、Django 多仓库路由提取、Java/Kotlin HTTP 消费者提取扩展、Java source/sink 模型、性能优化、PDG 跨仓库调用追踪、Kotlin fun interface 提取修复。新贡献者参与。"
key_points:
  - "相比 rc.12 缺少两项 HTTP 处理程序解析特性（内联 + 命名跨文件）"
  - "保留 Python/Java 污点分析模型、Kotlin Spring 与 Django 路由提取"
  - "包含 PDG 跨仓库调用追踪与性能优化"
tags: [code-analysis, release-candidate, taint-analysis, kotlin]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.10

GitNexus v1.6.9-rc.10 发布，为目标稳定版 1.6.9 的第 10 个 RC 版本。相比 rc.12 缺少「通过调用点行号解析内联 HTTP 提供者处理程序」与「跨文件命名 HTTP 处理程序解析」两项特性。包含 Python 污点分析模型、修复 Ladybug 双重释放崩溃、Kotlin Spring HTTP 消费者提取、Django 多仓库路由提取、Java/Kotlin HTTP 消费者提取扩展、Java source/sink 模型、性能优化、PDG 跨仓库调用追踪、Kotlin fun interface 提取修复。新贡献者参与。

### 重點
- 相比 rc.12 缺少两项 HTTP 处理程序解析特性（内联 + 命名跨文件）
- 保留 Python/Java 污点分析模型、Kotlin Spring 与 Django 路由提取
- 包含 PDG 跨仓库调用追踪与性能优化

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.10)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.10 \n Target base: 1.6.9 (rc #10 )\n Source commit (main): d27fd11 \n Release commit (versioned tree): 2ff0ac3 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 
 Full Changelog : v1.6.8...v1.6.9-rc.10

</details>