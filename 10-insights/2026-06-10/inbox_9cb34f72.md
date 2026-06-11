---
id: inbox_9cb34f72
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_9cb34f72]]"
title: "Release Candidate v1.6.8-rc.7"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.7
source: gitnexus-releases
published_at: 2026-06-10T10:40:55+00:00
fetched_at: 2026-06-11T00:22:23.758151+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.8-rc.7 是第 7 個預發行版本，聚焦於倉庫索引引擎的基礎修復。修復向量索引建立、Docker 資源打包、Java Spring 路由提取、多分支索引、衝擊分析精度等核心功能。相較後續 rc，本版本未包含 embeddings 依賴解析與解析器穩定性改進，代表整個 rc 週期中最早的功能分層。"
key_points:
  - "向量索引統一化：改用 connection.query 而非預備語句路徑"
  - "Java 路由提取：支援 Spring @RouteMapping 註解提取為 Route 節點"
  - "多分支索引：程式碼分析跨越不同 Git 分支"
tags: [code-analysis, java-analysis, repository-indexing, release-candidate]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.7

GitNexus v1.6.8-rc.7 是第 7 個預發行版本，聚焦於倉庫索引引擎的基礎修復。修復向量索引建立、Docker 資源打包、Java Spring 路由提取、多分支索引、衝擊分析精度等核心功能。相較後續 rc，本版本未包含 embeddings 依賴解析與解析器穩定性改進，代表整個 rc 週期中最早的功能分層。

### 重點
- 向量索引統一化：改用 connection.query 而非預備語句路徑
- Java 路由提取：支援 Spring @RouteMapping 註解提取為 Route 節點
- 多分支索引：程式碼分析跨越不同 Git 分支

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.7)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.8-rc.7

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.7 \n Target base: 1.6.8 (rc #7 )\n Source commit (main): ae5ec94 \n Release commit (versioned tree): f190e2f \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 fix(embeddings): create VECTOR index via conn.query, not the prepared path ( #2114 ) by @magyargergo in #2133 
 fix(docker): ship runtime-needed published assets (hooks/, skills/) into the image ( #2130 ) by @magyargergo in #2132 
 fix(hooks): silence MCP-owned-DB augment skip for strict hook runners ( #1913 ) by @magyargergo in #2134 
 feat(ingestion): Java Spring route annotation → Route node extraction by @henry201605 in #2078 
 feat: multi-branch indexing and branch-scoped querying ( #2106 ) by @magyargergo in #2137 
 fix: stop impact()/route_map under-reporting blast radius ( #2129 , #1858 , #1589 / #1852 ) by @magyargergo in #2136 
 
 Full Changelog : v1.6.7...v1.6.8-rc.7

</details>