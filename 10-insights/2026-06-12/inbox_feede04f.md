---
id: inbox_feede04f
date: 2026-06-12
source_ref: "[[00-inbox/2026-06-12/0336-gitnexus-releases-release-candidate-v1-6-8-rc-21-d2bb]]"
title: "Release Candidate v1.6.8-rc.21"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.21
source: gitnexus-releases
published_at: 2026-06-12T06:57:12+00:00
fetched_at: 2026-06-13T03:42:23.383726+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.8-rc.21 首次引入完整的污點分析引擎，涵蓋 18 項改進。新增 intra-procedural 污點追蹤（含 Express/Node 內建模型、38 個測試場景）、Java Spring 路由提取、多分支索引與查詢、TypeScript/JavaScript 控制流圖層、循環導入檢測。修復 VECTOR 索引創建、Docker 資源打包（hooks/ 和 skills/）、MCP 增強、大型儲存庫解析崩潰、影響半徑計算低報告問題。此 RC 代表代碼分析能力的重大躍進。"
key_points:
  - "首度發布污點分析引擎：完整的 intra-procedural 實現，內建 Express/Node source/sink 模型，38 個測試場景驗證準確性"
  - "多分支索引與查詢：支持不同分支的獨立索引與作用域查詢，擴展 GitNexus 在多版本環境的適用性"
  - "基礎設施改進：Docker 鏡像現包含 hooks/ 和 skills/ 資源；VECTOR 索引創建改為 conn.query 以提升穩定性"
tags: [gitnexus, taint-analysis, security-analysis, code-indexing, multi-branch]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.21

GitNexus v1.6.8-rc.21 首次引入完整的污點分析引擎，涵蓋 18 項改進。新增 intra-procedural 污點追蹤（含 Express/Node 內建模型、38 個測試場景）、Java Spring 路由提取、多分支索引與查詢、TypeScript/JavaScript 控制流圖層、循環導入檢測。修復 VECTOR 索引創建、Docker 資源打包（hooks/ 和 skills/）、MCP 增強、大型儲存庫解析崩潰、影響半徑計算低報告問題。此 RC 代表代碼分析能力的重大躍進。

### 重點
- 首度發布污點分析引擎：完整的 intra-procedural 實現，內建 Express/Node source/sink 模型，38 個測試場景驗證準確性
- 多分支索引與查詢：支持不同分支的獨立索引與作用域查詢，擴展 GitNexus 在多版本環境的適用性
- 基礎設施改進：Docker 鏡像現包含 hooks/ 和 skills/ 資源；VECTOR 索引創建改為 conn.query 以提升穩定性

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.21)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.21 \n Target base: 1.6.8 (rc #21 )\n Source commit (main): 14397dd \n Release commit (versioned tree): b9e74bd \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 fix(hooks): bound db-lock probe subprocesses and gate probe behind hook slot ( #2163 ) by @Minidoracat in #2165 
 feat(cli): add circular import cycle check by @azizur100389 in #2166 
 chore(devcontainer): remove version pin from AI CLIs by @magyargergo in #2174 
 feat(taint): intra-procedural taint analysis ( #2083 ) by @magyargergo in #2164 
 
 New Contributors 
 
 @buihongduc132 made their first contribution in #2124 
 
 Full Changelog : v1.6.7...v1.6.8-rc.21

</details>