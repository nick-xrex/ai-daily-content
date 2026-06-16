---
id: inbox_af7e6a97
date: 2026-06-15
source_ref: "[[00-inbox/.../inbox_af7e6a97]]"
title: "Release Candidate v1.6.8-rc.42"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.42
source: gitnexus-releases
published_at: 2026-06-15T21:53:49+00:00
fetched_at: 2026-06-16T00:43:14.381588+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 發布 v1.6.8-rc.42 release candidate，引入高級程式分析能力。核心創新包括：跨過程污點追蹤（interprocedural taint）基於函數摘要實現可擴展分析、控制流圖（CFG）與程式依賴圖（PDG）建構支援 TypeScript/JavaScript、到達定義（reaching-defs）資料流分析採用 SSA 稀疏表示大幅降低計算成本、Java Spring 路由註解自動抽取、多分支索引與範圍化查詢支援更準確的 impact 分析。亦新增循環匯入偵測、修復向量索引、Docker 發佈、hook 運作、大型儲存庫解析等問題。"
key_points:
  - "跨過程污點追蹤基於函數摘要（function summaries）實現可擴展的安全性分析，無需全程式掃描，支援更大規模代碼庫分析"
  - "程式依賴圖（PDG）整合控制依賴（via post-dominators + Ferrante 演算法）與資料依賴，支援更精細的漏洞偵測與程式理解"
  - "SSA 稀疏到達定義（reaching-defs）取代密集集合表示，測試顯示圖形資料庫發送與持久化時間顯著下降"
tags: [gitnexus, program-analysis, taint-analysis, cfg-pdg, code-intelligence]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.42

GitNexus 發布 v1.6.8-rc.42 release candidate，引入高級程式分析能力。核心創新包括：跨過程污點追蹤（interprocedural taint）基於函數摘要實現可擴展分析、控制流圖（CFG）與程式依賴圖（PDG）建構支援 TypeScript/JavaScript、到達定義（reaching-defs）資料流分析採用 SSA 稀疏表示大幅降低計算成本、Java Spring 路由註解自動抽取、多分支索引與範圍化查詢支援更準確的 impact 分析。亦新增循環匯入偵測、修復向量索引、Docker 發佈、hook 運作、大型儲存庫解析等問題。

### 重點
- 跨過程污點追蹤基於函數摘要（function summaries）實現可擴展的安全性分析，無需全程式掃描，支援更大規模代碼庫分析
- 程式依賴圖（PDG）整合控制依賴（via post-dominators + Ferrante 演算法）與資料依賴，支援更精細的漏洞偵測與程式理解
- SSA 稀疏到達定義（reaching-defs）取代密集集合表示，測試顯示圖形資料庫發送與持久化時間顯著下降

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.42)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.8-rc.42

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.42 \n Target base: 1.6.8 (rc #42 )\n Source commit (main): 067c73b \n Release commit (versioned tree): da536a6 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 fix(ci): align tree-sitter readiness + grammar-update workflows on a shared manifest ( #858 ) by @magyargergo in #2187 
 feat(pdg): control dependence — post-dominators + CDG (Ferrante) [M5 #2085 ] by @magyargergo in #2188 
 fix(group): pin repos during sync so large groups resolve cross-links by @magyargergo in #2191 
 fix(cli): preserve trailing spaces in git roots by @koriyoshi2041 in #2192 
 feat(mcp): add trace tool for shortest call path between symbols by @goutham80808 in #2173 
 fix: detect single-ancestor method overrides in MRO processor by @ChunxueLi in #2199 
 feat(cfg): PDG/CFG visitors for all supported languages ( #2195 ) by @magyargergo in #2197 
 feat(cfg): model value-position branches as control dependence ( #2205 , #2207 ) by @magyargergo in #2211 
 perf(cfg): SSA-sparse reaching-defs to replace the dense-set worklist ( #2201 ) by @magyargergo in #2212 
 perf(lbug): cut graph-DB emit/persistence wall time ( #2203 ) by @magyargergo in #2215 
 
 New Contributors 
 
 @buihongduc132 made their first contribution in #2124 
 @blueroseslol made their first contribution in #2141 
 @koriyoshi2041 made their first contribution in #2192 
 @goutham80808 made their first contribution in #2173 
 @ChunxueLi made their first contribution in #2199 
 
 Full Changelog : v1.6.7...v1.6.8-rc.42

</details>