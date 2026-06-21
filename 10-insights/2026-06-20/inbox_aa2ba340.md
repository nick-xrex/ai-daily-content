---
id: inbox_aa2ba340
date: 2026-06-20
source_ref: "[[00-inbox/.../inbox_aa2ba340]]"
title: "v1.6.8"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8
source: gitnexus-releases
published_at: 2026-06-20T20:40:12+00:00
fetched_at: 2026-06-21T02:26:57.000117+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.8 發布為主要穩定版本，核心創新是「程式依存圖」（Program Dependence Graph, PDG）導入。PDG 驅動的影響分析以 opt-in --pdg 模式啟用，用語句級別和跨程序程式切片計算爆炸範圍，經變異預言機驗證確保準確度。完整的 PDG 基礎架構涵蓋所有支援語言，包括控制流圖（CFG）、到達定義（reaching-definitions）資料依存和控制依存（Ferrante 風格控制依存圖）。污點分析支援單程序追蹤和跨程序傳播。多分支索引允許每個分支單獨分析和查詢，保持主分支佈局不變。新增私有倉庫支援（GitHub PAT + Azure DevOps）、MCP HTTP 伺服器、追蹤工具、Java Spring 路由提取等功能。效能優化包括流式 PDG 發射處理核心規模倉庫和 SSA 稀疏到達定義求解器。"
key_points:
  - "PDG 驅動影響分析（opt-in --pdg 模式）：語句級別與跨程序程式切片，經變異預言機驗證精確計算爆炸範圍"
  - "完整 PDG 基礎架構：CFG、reaching-definitions、control dependence 跨全語言覆蓋，污點分析支援單/跨程序追蹤"
  - "多分支索引、私有倉庫支援（PAT/Azure DevOps）、MCP HTTP 伺服器追蹤工具、Java Spring 路由提取、流式 PDG 發射和 SSA 稀疏求解器效能優化"
tags: [gitnexus, pdg, program-dependence-graph, code-analysis, impact-analysis]
topics: []
importance: 5
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## v1.6.8

GitNexus v1.6.8 發布為主要穩定版本，核心創新是「程式依存圖」（Program Dependence Graph, PDG）導入。PDG 驅動的影響分析以 opt-in --pdg 模式啟用，用語句級別和跨程序程式切片計算爆炸範圍，經變異預言機驗證確保準確度。完整的 PDG 基礎架構涵蓋所有支援語言，包括控制流圖（CFG）、到達定義（reaching-definitions）資料依存和控制依存（Ferrante 風格控制依存圖）。污點分析支援單程序追蹤和跨程序傳播。多分支索引允許每個分支單獨分析和查詢，保持主分支佈局不變。新增私有倉庫支援（GitHub PAT + Azure DevOps）、MCP HTTP 伺服器、追蹤工具、Java Spring 路由提取等功能。效能優化包括流式 PDG 發射處理核心規模倉庫和 SSA 稀疏到達定義求解器。

### 重點
- PDG 驅動影響分析（opt-in --pdg 模式）：語句級別與跨程序程式切片，經變異預言機驗證精確計算爆炸範圍
- 完整 PDG 基礎架構：CFG、reaching-definitions、control dependence 跨全語言覆蓋，污點分析支援單/跨程序追蹤
- 多分支索引、私有倉庫支援（PAT/Azure DevOps）、MCP HTTP 伺服器追蹤工具、Java Spring 路由提取、流式 PDG 發射和 SSA 稀疏求解器效能優化

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v1.6.8

GitNexus v1.6.8 
 
 The Program Dependence Graph release. Opt-in PDG-backed impact analysis and taint tracking, built out across every supported language — plus multi-branch indexing, private-repo cloning, and a streamable-HTTP MCP server. 
 
 ✨ Highlights 
 
 🎯 PDG-backed impact analysis — impact gains an opt-in mode: 'pdg' that runs statement-level and inter-procedural program slicing for a far more precise blast radius, validated by a mutation oracle. The default call-graph mode is unchanged. ( #2227 ) 
 🧬 A full Program Dependence Graph substrate — control-flow graphs, reaching-definitions data dependence, and control dependence (post-dominators + a Ferrante-style CDG) now exist for every supported language. All of it is opt-in behind --pdg ; a default analyze run stays byte-identical. ( #2197 , #2160 , #2188 , #2211 ) 
 🔬 Taint analysis — intra-procedural tracking over the PDG plus inter-procedural taint via function summaries propagated over resolved CALLS edges. ( #2164 , #2179 ) 
 🌿 Multi-branch indexing — analyze and query a repository per branch, each stored under its own subdirectory, with the primary-branch layout untouched. ( #2137 ) 
 🔐 Private repositories — clone private GitHub repos with a PAT, with Azure DevOps Server support. ( #2223 ) 
 🔌 MCP gains a trace tool and an HTTP server — shortest call path between two symbols, and gitnexus mcp --http over Streamable HTTP (with legacy SSE). ( #2173 , #2141 ) 
 
 
 🚀 Added 
 
 PDG-backed impact analysis (opt-in) — impact gains a mode: 'pdg' that runs statement-level and inter-procedural program slicing for far more precise blast radius, with resolved-callee-id soundness and validation by a mutation oracle; the default call-graph mode is unchanged ( #2227 ) 
 Program Dependence Graph substrate across the language matrix — a control-flow-graph layer landed for TS/JS ( #2099 ) and was extended to PDG/CFG visitors for every supported language ( #2197 ); on top of it an intra-procedural REACHING_DEF data-dependence layer ( #2160 ), value-position branches ( if / when / switch / match / try used as expressions) modeled as control dependence ( #2211 ), and full control dependence via post-dominators + a Ferrante-style CDG ( #2188 ). All layers are opt-in behind --pdg ; a default analyze run stays byte-identical ( #2082 , #2085 , #2205 , #2207 , #2195 ) 
 Taint analysis — intra-procedural taint tracking over the PDG ( #2164 ) plus inter-procedural taint via function summaries propagated over resolved CALLS edges ( #2179 ) ( #2083 , #2084 ) 
 Multi-branch indexing and branch-scoped querying — analyze and query a repository per branch, with each branch stored under its own subdirectory and the primary branch layout left unchanged ( #2137 , #2106 ) 
 Private GitHub repos via PAT + Azure DevOps Server support — gitnexus analyze can clone private GitHub repositories with a personal access token and supports Azure DevOps Server remotes ( #2223 , #2076 , #2210 ) 
 MCP trace tool — returns the shortest call path between two symbols ( #2173 ) 
 MCP HTTP server — gitnexus mcp --http exposes the server over Streamable HTTP with legacy SSE transport support ( #2141 ) 
 HTTP route extraction — Java Spring route annotations are now extracted into Route nodes ( #2078 ), and the HTTP method is persisted on each Route node ( #2234 , #2138 ) 
 gitnexus analyze circular import cycle check ( #2166 ) 
 gitnexus analyze embeddings flags — --embeddings-baseurl , --embeddings-model , --embeddings-auth-token , and --embeddings-dims to point analyze at a custom embeddings provider ( #2140 ) 
 gitnexus setup coding-agent integration selection — choose which coding-agent integrations to install during setup ( #2168 ) 
 C++ CUDA source extensions parsed — .cu / .cuh files are now ingested ( #2213 ) 
 
 🐛 Fixed 
 
 impact() / route_map under-reporting blast radius — name-resolution gaps that caused callers and routes to be dropped are fixed, with ambiguous symbols reported per-candidate ( #2136 , #2129 , #1858 , #1852 ) 
 Single-ancestor method override detection in the MRO processor ( #2199 ) 
 MCP query / cypher parameter names — renamed so Claude Code can invoke them, while still accepting the legacy parameter ( #2186 ) 
 C++ overload resolution — homogeneous braced-init overloads are now ranked ( #2214 ), deleted overload winners are suppressed ( #2094 ), and the C++ hook layer handles pack-base comments and missing hook overrides ( #2247 ) 
 Large-repo analyze crash — the pipeline now survives non-cloneable worker results instead of aborting ( #2135 , #2112 ) 
 Embeddings — onnxruntime-common resolves under pnpm-strict / pnpm dlx installs ( #2139 , #307 ), and the VECTOR index is created via conn.query rather than the prepared-statement path that silently skipped it ( #2114 ) 
 Vendored tree-sitter grammars — loaded from vendor/ by absolute path so analyze finds them regardless of CWD ( #2144 , #2111 ) 
 Registry wipe on transient I/O errors prevented — a failed read no longer clears the repository registry ( #2124 ) 
 Server roots resolve from GITNEXUS_HOME — clone, upload, and mapping roots honor the configured home directory ( #2229 ) 
 Wiki generation keeps the graph DB pinned so it is not evicted mid-generation ( #2232 ) 
 Group sync pins repositories so large groups resolve their cross-repo links ( #2191 ) 
 Web viewer — a chat-only mode for large projects prevents the WebUI from hanging ( #2185 , #2178 ), and the broken Browse-for-folder control was replaced with an upload directory picker ( #1850 ) 
 Hooks — the augment CLI child is wrapped in the orphan guard ( #2169 ), db-lock probe subprocesses are bounded and gated behind a hook slot ( #2165 ), and the MCP-owned-DB augment-skip diagnostic is silenced for strict hook runners ( #2134 , #2163 , #1913 ) 
 Docker image ships runtime-needed published assets — hooks/ and skills/ are copied into the image so gitnexus analyze no longer crashes with MODULE_NOT_FOUND ( #2132 , #2130 ) 
 gitnexus analyze preserves trailing spaces in git roots ( #2192 ) 
 Write-route origin guard scoped to the server's own bound host ( #2172 ) 
 Impact PDG Mutation Report workflow — fixed three latent oracle bugs (dist-CLI invocation under Node ≥ 22.18 type-stripping, undeclared @babel/* deps, and a recall-gated check filter) so the mutation oracle CI runs green ( #2258 ) 
 
 🔧 Changed 
 
 tree-sitter readiness/summary CI hardened — readiness and grammar-update workflows aligned on a shared manifest ( #2187 , #858 ), readiness summary counts kept current ( #2196 ), and the summary now fails on parse drift ( #2246 ) 
 Devcontainer simplified — Dockerfile and devcontainer.json no longer pin version args for the AI CLIs ( #2174 ) 
 
 ⚡ Performance 
 
 Graph-DB emit/persistence — cut overall emit/persistence wall time ( #2215 ) and overlap node COPY with relationship emit ( #2226 ) ( #2203 ) 
 PDG/CFG emit — streaming/chunked PDG graph emit for full-kernel-scale repos ( #2216 , #2202 ) and an SSA-sparse reaching-defs solver replacing the dense-set worklist ( #2212 , #2201 ) 
 Hook db-lock scan — cmdline-first on Linux, dropping the lsof fallback ( #2183 , #2180 ) 
 
 
 📦 Chore / Dependencies — 30 dependency &amp; CI-action bumps
 
 gitnexus runtime — hono 4.12.23 → 4.12.26 ( #2244 ), tar 7.5.13 → 7.5.16 ( #2218 ), protobufjs 7.5.8 → 7.6.4 ( #2219 ), js-yaml 4.1.1 → 4.2.0 ( #2097 , #2217 ), and an npm_and_yarn security group, 3 updates ( #2220 ) 
 gitnexus dev — vitest 4.1.8 → 4.1.9 ( #2249 ), @vitest/coverage-v8 ( #2250 ), esbuild 0.28.0 → 0.28.1 ( #2182 ), and @types/node ( #2128 , #2222 ) 
 gitnexus-web — react-dom 19.2.6 → 19.2.7 ( #2240 ), langchain 1.4.2 → 1.4.4 ( #2149 ), @langchain/langgraph ( #2235 ), @langchain/ollama ( #2236 ), mnemonist 0.39.8 → 0.40.4 ( #2237 ), lucide-react ( #2238 ), sigma 3.0.2 → 3.0.3 ( #2151 ), dompurify 3.4.7 → 3.4.8 ( #2150 , #2245 ), @vercel/node ( #2156 ), and @vitest/coverage-v8 ( #2153 ) 
 eval — aiohttp ( #2224 ) 
 CI actions — gitleaks/gitleaks-action 2.3.9 → 3.0.0 ( #2241 ), github/codeql-action 4.36.0 → 4.36.2 ( #2242 ), actions/checkout 6.0.2 → 6.0.3 ( #2152 ), actions/attest-build-provenance 2.4.0 → 4.1.0 ( #2158 ), docker/setup-qemu-action 4.0.0 → 4.1.0 ( #2159 ), release-drafter/release-drafter 7.3.0 → 7.3.1 ( #2157 ), and actions/setup-python 5.6.0 → 6.2.0 ( #2155 ) 
 
 
 
 📥 Upgrade 
 npm install -g gitnexus@1.6.8 
 Then re-index to pick up the new graph layers: 
 gitnexus analyze # standard re-index 
gitnexus analyze --pdg # opt in to the PDG/taint layers 
 Full changelog: v1.6.7...v1.6.8

</details>