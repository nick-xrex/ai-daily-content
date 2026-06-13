---
id: inbox_cce9b725
date: 2026-06-13
source_ref: "[[00-inbox/2026-06-13/2200-gitnexus-releases-release-candidate-v1-6-8-rc-30-a2cf]]"
title: "Release Candidate v1.6.8-rc.30"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.30
source: gitnexus-releases
published_at: 2026-06-13T13:25:48+00:00
fetched_at: 2026-06-13T22:04:06.580986+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.8-rc.30 發佈，為 1.6.8 版本的第 30 個預發佈候選版本。包含控制流圖層新增、MCP HTTP 伺服器實裝、向量索引修復、Docker 資源部署改善、Java Spring 支援等。相較 rc.31，缺少後續新增的嵌入基址配置參數。"
key_points:
  - "TypeScript/JavaScript 控制流圖層（CFG）新增與資料依賴分析"
  - "MCP HTTP 伺服器實裝，支援 Claude Code 整合"
  - "向量索引、Docker 部署、Java 路由支援改善"
tags: [gitnexus, mcp-integration, code-analysis, release-candidate]
topics: [agents.mcp]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.30

GitNexus v1.6.8-rc.30 發佈，為 1.6.8 版本的第 30 個預發佈候選版本。包含控制流圖層新增、MCP HTTP 伺服器實裝、向量索引修復、Docker 資源部署改善、Java Spring 支援等。相較 rc.31，缺少後續新增的嵌入基址配置參數。

### 重點
- TypeScript/JavaScript 控制流圖層（CFG）新增與資料依賴分析
- MCP HTTP 伺服器實裝，支援 Claude Code 整合
- 向量索引、Docker 部署、Java 路由支援改善

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.30)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.30 \n Target base: 1.6.8 (rc #30 )\n Source commit (main): 89ffa71 \n Release commit (versioned tree): f8db952 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 fix(web): chat-only mode for large projects to prevent WebUI hang ( #2178 ) by @magyargergo in #2185 
 perf(hooks): cmdline-first Linux db-lock scan, drop the lsof fallback ( #2180 ) by @Minidoracat in #2183 
 feat(cli): add --embeddings-baseurl/-model/-auth-token/-dims flags to analyze by @blueroseslol in #2140 
 
 New Contributors 
 
 @buihongduc132 made their first contribution in #2124 
 @blueroseslol made their first contribution in #2141 
 
 Full Changelog : v1.6.7...v1.6.8-rc.30

</details>