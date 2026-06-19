---
id: inbox_7ad36759
date: 2026-06-18
source_ref: "[[00-inbox/2026-06-18/2200-gitnexus-releases-release-candidate-v1-6-8-rc-49-259a]]"
title: "Release Candidate v1.6.8-rc.49"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.49
source: gitnexus-releases
published_at: 2026-06-18T04:31:55+00:00
fetched_at: 2026-06-18T22:04:51.207706+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.8-rc.49 發布候選版本。本版本包含多項技術改進：多分支索引、控制流圖（CFG）分析、污點分析（taint analysis）、HTTP MCP 伺服器支援。係軟體開發工具發布，不屬 AI 新聞。"
key_points:
tags: []
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.49

GitNexus v1.6.8-rc.49 發布候選版本。本版本包含多項技術改進：多分支索引、控制流圖（CFG）分析、污點分析（taint analysis）、HTTP MCP 伺服器支援。係軟體開發工具發布，不屬 AI 新聞。

### 重點

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.49)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.49 \n Target base: 1.6.8 (rc #49 )\n Source commit (main): e33f908 \n Release commit (versioned tree): 85592e5 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 perf(cfg): streaming/chunked PDG graph emit for full-kernel-scale repos ( #2202 ) by @magyargergo in #2216 
 feat(analyze): private GitHub repos via PAT + Azure DevOps Server support ( #2076 , #2210 ) by @magyargergo in #2223 
 feat(cpp): parse CUDA source extensions by @azizur100389 in #2213 
 perf(lbug): overlap node COPY with relationship emit ( #2203 ) by @magyargergo in #2226 
 fix(cpp): rank homogeneous braced-init overloads by @azizur100389 in #2214 
 fix(wiki): keep graph DB pinned during generation by @koriyoshi2041 in #2232 
 ci: keep tree-sitter readiness summary counts current by @koriyoshi2041 in #2196 
 
 New Contributors 
 
 @buihongduc132 made their first contribution in #2124 
 @blueroseslol made their first contribution in #2141 
 @koriyoshi2041 made their first contribution in #2192 
 @goutham80808 made their first contribution in #2173 
 @ChunxueLi made their first contribution in #2199 
 
 Full Changelog : v1.6.7...v1.6.8-rc.49

</details>