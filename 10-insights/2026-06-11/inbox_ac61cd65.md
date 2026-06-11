---
id: inbox_ac61cd65
date: 2026-06-11
source_ref: "[[00-inbox/2026-06-11/2200-gitnexus-releases-release-candidate-v1-6-8-rc-17-b3f9]]"
title: "Release Candidate v1.6.8-rc.17"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.17
source: gitnexus-releases
published_at: 2026-06-11T05:04:35+00:00
fetched_at: 2026-06-11T22:04:44.949606+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.8-rc.17 發佈，是預釋行版本的早期迭代。此版本包含多項代碼分析增強，新增 TypeScript/JavaScript 的控制流圖層和資料依賴分析能力，支持對複雜程式碼結構的理解。同時支持多分支索引和分支範圍查詢，改進對複雜倉庫結構的處理能力。修復包括 embedding 索引建立、Docker 資產發佈、MCP 鉤子靜音等 bug，增強工具的穩定性和相容性。"
key_points:
  - "新增 TS/JS 控制流圖和資料依賴分析層"
  - "支持多分支索引和分支範圍查詢機制"
  - "修復 embedding、Docker、MCP 等組件的多個 bug"
tags: [gitnexus, release-candidate, code-analysis]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.17

GitNexus v1.6.8-rc.17 發佈，是預釋行版本的早期迭代。此版本包含多項代碼分析增強，新增 TypeScript/JavaScript 的控制流圖層和資料依賴分析能力，支持對複雜程式碼結構的理解。同時支持多分支索引和分支範圍查詢，改進對複雜倉庫結構的處理能力。修復包括 embedding 索引建立、Docker 資產發佈、MCP 鉤子靜音等 bug，增強工具的穩定性和相容性。

### 重點
- 新增 TS/JS 控制流圖和資料依賴分析層
- 支持多分支索引和分支範圍查詢機制
- 修復 embedding、Docker、MCP 等組件的多個 bug

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.17)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.17 \n Target base: 1.6.8 (rc #17 )\n Source commit (main): bde340a \n Release commit (versioned tree): 4e03a1e \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 fix(storage): prevent registry wipe on transient I/O errors by @buihongduc132 in #2124 
 fix(cpp): suppress deleted overload winners by @azizur100389 in #2094 
 feat(ingestion): add control-flow-graph layer for TS/JS ( #2081 ) by @magyargergo in #2099 
 fix(web): replace broken Browse-for-folder with upload directory picker by @magyargergo in #1850 
 feat(cfg): intra-procedural REACHING_DEF data-dependence layer ( #2082 ) by @magyargergo in #2160 
 
 New Contributors 
 
 @buihongduc132 made their first contribution in #2124 
 
 Full Changelog : v1.6.7...v1.6.8-rc.17

</details>