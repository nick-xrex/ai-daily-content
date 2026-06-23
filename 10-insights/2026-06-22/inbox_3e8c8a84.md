---
id: inbox_3e8c8a84
date: 2026-06-22
source_ref: "[[00-inbox/2026-06-22/2203-gitnexus-releases-release-candidate-v1-6-9-rc-5-314e]]"
title: "Release Candidate v1.6.9-rc.5"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.5
source: gitnexus-releases
published_at: 2026-06-22T09:04:21+00:00
fetched_at: 2026-06-22T23:23:45.102691+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.9-rc.5 發布，新增 Python source/sink 污點追蹤模型、Kotlin Spring HTTP 消費者提取、Django 路由提取、Java/Kotlin HTTP 消費者提取擴展；並修復 LadybugDB double-free 崩潰及連線序列化問題。"
key_points:
  - "新增 Python source/sink 污點追蹤模型，擴展 Python 程式碼分析能力"
  - "Kotlin Spring HTTP 消費者提取達到與 Java 功能對等"
  - "修復 LadybugDB 雙重解放（double-free）導致的析構函數崩潰"
tags: [gitnexus, code-analysis, python, kotlin, java]
topics: []
importance: 1
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.9-rc.5

GitNexus v1.6.9-rc.5 發布，新增 Python source/sink 污點追蹤模型、Kotlin Spring HTTP 消費者提取、Django 路由提取、Java/Kotlin HTTP 消費者提取擴展；並修復 LadybugDB double-free 崩潰及連線序列化問題。

### 重點
- 新增 Python source/sink 污點追蹤模型，擴展 Python 程式碼分析能力
- Kotlin Spring HTTP 消費者提取達到與 Java 功能對等
- 修復 LadybugDB 雙重解放（double-free）導致的析構函數崩潰

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.5 \n Target base: 1.6.9 (rc #5 )\n Source commit (main): 77741fe \n Release commit (versioned tree): b23af10 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(taint): add Python source/sink model by @azizur100389 in #2253 
 fix(lbug): stop --pdg analyze double-free (skip LadybugDB close-destructor crash) + harden connection serialization by @magyargergo in #2264 
 feat(group): Kotlin Spring HTTP consumer extraction + provider parity with Java by @glier in #2254 
 feat(group): Support Django route extraction for multi-repo by @HuyNguyenDinh in #1836 
 feat(group): expand Java and Kotlin HTTP consumer extraction (re #1888 ) by @magyargergo in #2268 
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 
 Full Changelog : v1.6.8...v1.6.9-rc.5

</details>