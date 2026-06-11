---
id: inbox_a4eb7d4c
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_a4eb7d4c]]"
title: "Release Candidate v1.6.8-rc.10"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.10
source: gitnexus-releases
published_at: 2026-06-10T13:36:56+00:00
fetched_at: 2026-06-11T00:22:23.754756+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.8-rc.10 是第 10 個預發行版本，包含與 rc.11 相同的核心修復：向量索引建立、Docker 資源、MCP 資料庫擴增跳過、Java 路由提取、多分支索引、衝擊分析精度、embeddings 依賴解析等改進。作為預發行版本，用於社群早期測試穩定性。"
key_points:
  - "VECTOR 索引建立機制統一化，避免預備語句路徑導致的失敗"
  - "多分支索引支援：程式碼分析跨越多個 Git 分支"
  - "embeddings 依賴解析：修復 pnpm-strict 與 pnpm dlx 下的 onnxruntime-common 載入問題"
tags: [code-analysis, repository-indexing, developer-tools, release-candidate]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.10

GitNexus v1.6.8-rc.10 是第 10 個預發行版本，包含與 rc.11 相同的核心修復：向量索引建立、Docker 資源、MCP 資料庫擴增跳過、Java 路由提取、多分支索引、衝擊分析精度、embeddings 依賴解析等改進。作為預發行版本，用於社群早期測試穩定性。

### 重點
- VECTOR 索引建立機制統一化，避免預備語句路徑導致的失敗
- 多分支索引支援：程式碼分析跨越多個 Git 分支
- embeddings 依賴解析：修復 pnpm-strict 與 pnpm dlx 下的 onnxruntime-common 載入問題

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.10)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.8-rc.10

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.10 \n Target base: 1.6.8 (rc #10 )\n Source commit (main): 2870aa6 \n Release commit (versioned tree): abfe29b \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 fix(embeddings): create VECTOR index via conn.query, not the prepared path ( #2114 ) by @magyargergo in #2133 
 fix(docker): ship runtime-needed published assets (hooks/, skills/) into the image ( #2130 ) by @magyargergo in #2132 
 fix(hooks): silence MCP-owned-DB augment skip for strict hook runners ( #1913 ) by @magyargergo in #2134 
 feat(ingestion): Java Spring route annotation → Route node extraction by @henry201605 in #2078 
 feat: multi-branch indexing and branch-scoped querying ( #2106 ) by @magyargergo in #2137 
 fix: stop impact()/route_map under-reporting blast radius ( #2129 , #1858 , #1589 / #1852 ) by @magyargergo in #2136 
 fix(embeddings): resolve onnxruntime-common under pnpm-strict / pnpm dlx ( #307 ) by @magyargergo in #2139 
 fix(parse): survive non-cloneable worker results so large-repo analyze doesn't crash ( #2112 ) by @magyargergo in #2135 
 fix(grammars): load vendored tree-sitter grammars from vendor/ by absolute path ( #2111 ) by @magyargergo in #2144 
 
 Full Changelog : v1.6.7...v1.6.8-rc.10

</details>