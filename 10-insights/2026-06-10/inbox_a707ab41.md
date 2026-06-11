---
id: inbox_a707ab41
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_a707ab41]]"
title: "Release Candidate v1.6.8-rc.8"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.8
source: gitnexus-releases
published_at: 2026-06-10T11:28:03+00:00
fetched_at: 2026-06-11T00:22:23.757520+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.8-rc.8 是第 8 個預發行版本，修復向量索引建立、Docker 資源打包、Java Spring 路由提取、多分支索引、衝擊分析精度等核心功能。未包含後續 rc 版本中的 embeddings 依賴與解析器改進，主要聚焦於倉庫索引引擎的基礎功能測試。"
key_points:
  - "向量索引建立改進：統一使用 conn.query 避免預備語句相依性"
  - "多分支索引支援：程式碼分析跨越 Git 分支邊界"
  - "Docker 環境支援：確保執行時所需的 hooks 與 skills 資源包含"
tags: [code-analysis, repository-indexing, release-candidate, version-control]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.8

GitNexus v1.6.8-rc.8 是第 8 個預發行版本，修復向量索引建立、Docker 資源打包、Java Spring 路由提取、多分支索引、衝擊分析精度等核心功能。未包含後續 rc 版本中的 embeddings 依賴與解析器改進，主要聚焦於倉庫索引引擎的基礎功能測試。

### 重點
- 向量索引建立改進：統一使用 conn.query 避免預備語句相依性
- 多分支索引支援：程式碼分析跨越 Git 分支邊界
- Docker 環境支援：確保執行時所需的 hooks 與 skills 資源包含

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.8)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.8-rc.8

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.8 \n Target base: 1.6.8 (rc #8 )\n Source commit (main): 7f0ab87 \n Release commit (versioned tree): 4db67ac \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 fix(embeddings): create VECTOR index via conn.query, not the prepared path ( #2114 ) by @magyargergo in #2133 
 fix(docker): ship runtime-needed published assets (hooks/, skills/) into the image ( #2130 ) by @magyargergo in #2132 
 fix(hooks): silence MCP-owned-DB augment skip for strict hook runners ( #1913 ) by @magyargergo in #2134 
 feat(ingestion): Java Spring route annotation → Route node extraction by @henry201605 in #2078 
 feat: multi-branch indexing and branch-scoped querying ( #2106 ) by @magyargergo in #2137 
 fix: stop impact()/route_map under-reporting blast radius ( #2129 , #1858 , #1589 / #1852 ) by @magyargergo in #2136 
 fix(embeddings): resolve onnxruntime-common under pnpm-strict / pnpm dlx ( #307 ) by @magyargergo in #2139 
 
 Full Changelog : v1.6.7...v1.6.8-rc.8

</details>