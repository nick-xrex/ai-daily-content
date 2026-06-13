---
id: inbox_a61dd786
date: 2026-06-13
source_ref: "[[00-inbox/2026-06-13/2200-gitnexus-releases-release-candidate-v1-6-8-rc-27-b55f]]"
title: "Release Candidate v1.6.8-rc.27"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.27
source: gitnexus-releases
published_at: 2026-06-13T09:48:34+00:00
fetched_at: 2026-06-13T22:05:36.078154+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 1.6.8-rc.27 發布，是指向 1.6.8 穩定版本的第 27 個候選版本。此版本包含 24 項提交修復及功能新增：VECTOR index 創建路徑改進、Docker 鏡像包含運行時資源（hooks/skills）、多分支索引和分支作用域查詢支持、TypeScript/JavaScript 控制流圖層、過程內外汙點分析、圓形導入檢查、MCP HTTP 伺服器（Streamable HTTP + SSE 傳輸）、MCP query/cypher 參數重命名以支持 Claude Code 調用。並修正了大型倉庫解析穩定性、embedding 索引生成、Docker 資源打包等多個生產問題。"
key_points:
  - "新增 gitnexus mcp --http 伺服器，支持 Streamable HTTP 和 SSE 傳輸；MCP 參數重命名（query/cypher）使 Claude Code 可直接調用"
  - "完整汙點分析堆疊：過程內汙點分析 (#2083) + 過程間汙點分析通過函數摘要 (#2084) + REACHING_DEF 控制流圖層 (#2082)"
  - "多分支索引與分支作用域查詢 (#2106)；修正 impact()/route_map 對程式碼變更波及面的誤報 (#2129)"
tags: [code-analysis, embeddings, mcp-integration, taint-analysis, static-analysis]
topics: [agents.mcp]
importance: 2
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.27

GitNexus 1.6.8-rc.27 發布，是指向 1.6.8 穩定版本的第 27 個候選版本。此版本包含 24 項提交修復及功能新增：VECTOR index 創建路徑改進、Docker 鏡像包含運行時資源（hooks/skills）、多分支索引和分支作用域查詢支持、TypeScript/JavaScript 控制流圖層、過程內外汙點分析、圓形導入檢查、MCP HTTP 伺服器（Streamable HTTP + SSE 傳輸）、MCP query/cypher 參數重命名以支持 Claude Code 調用。並修正了大型倉庫解析穩定性、embedding 索引生成、Docker 資源打包等多個生產問題。

### 重點
- 新增 gitnexus mcp --http 伺服器，支持 Streamable HTTP 和 SSE 傳輸；MCP 參數重命名（query/cypher）使 Claude Code 可直接調用
- 完整汙點分析堆疊：過程內汙點分析 (#2083) + 過程間汙點分析通過函數摘要 (#2084) + REACHING_DEF 控制流圖層 (#2082)
- 多分支索引與分支作用域查詢 (#2106)；修正 impact()/route_map 對程式碼變更波及面的誤報 (#2129)

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.27)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.27 \n Target base: 1.6.8 (rc #27 )\n Source commit (main): 9ff7337 \n Release commit (versioned tree): 5a56c3c \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 fix(hooks): wrap the augment CLI child in the orphan guard ( #2163 ) by @Minidoracat in #2169 
 feat(taint): interprocedural taint via function summaries over resolved CALLS ( #2084 ) by @magyargergo in #2179 
 feat(setup): select coding agent integrations by @azizur100389 in #2168 
 fix(ip): Scope write-route origin guard to server's own bound host by @Copilot in #2172 
 feat(mcp): add gitnexus mcp --http server with Streamable HTTP and legacy SSE transports by @blueroseslol in #2141 
 fix(mcp): rename query/cypher params so Claude Code can call them by @magyargergo in #2186 
 
 New Contributors 
 
 @buihongduc132 made their first contribution in #2124 
 @blueroseslol made their first contribution in #2141 
 
 Full Changelog : v1.6.7...v1.6.8-rc.27

</details>