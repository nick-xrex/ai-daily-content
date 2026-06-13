---
id: inbox_b9fed370
date: 2026-06-13
source_ref: "[[00-inbox/2026-06-13/2200-gitnexus-releases-release-candidate-v1-6-8-rc-25-c6f2]]"
title: "Release Candidate v1.6.8-rc.25"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.25
source: gitnexus-releases
published_at: 2026-06-13T07:27:22+00:00
fetched_at: 2026-06-13T22:05:36.083178+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 1.6.8-rc.25 發布，為 rc.26 前約 1.5 小時發行的候選版本，源自主分支 50cda61 commit。包含同樣的功能集合：embedding 索引穩定性修復、Docker 打包改進、Java Spring annotation 支持、多分支索引、impact analysis 精度改進、TypeScript/JavaScript 控制流圖、過程內汙點分析、圓形導入檢查等，反映同日內多輪快速迭代的設計成熟過程。"
key_points:
  - "Java Spring 框架 route annotation 自動提取為 Route 節點 (#2078)"
  - "embedding 索引創建與 Docker 資源包含的多層面穩定性改進"
  - "多分支索引 (#2106) 與衝擊分析誤報修正 (#2129)"
tags: [code-analysis, embeddings, java-spring, static-analysis]
topics: [agents.mcp]
importance: 2
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.25

GitNexus 1.6.8-rc.25 發布，為 rc.26 前約 1.5 小時發行的候選版本，源自主分支 50cda61 commit。包含同樣的功能集合：embedding 索引穩定性修復、Docker 打包改進、Java Spring annotation 支持、多分支索引、impact analysis 精度改進、TypeScript/JavaScript 控制流圖、過程內汙點分析、圓形導入檢查等，反映同日內多輪快速迭代的設計成熟過程。

### 重點
- Java Spring 框架 route annotation 自動提取為 Route 節點 (#2078)
- embedding 索引創建與 Docker 資源包含的多層面穩定性改進
- 多分支索引 (#2106) 與衝擊分析誤報修正 (#2129)

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.25)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.25 \n Target base: 1.6.8 (rc #25 )\n Source commit (main): 50cda61 \n Release commit (versioned tree): 1f4e937 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @buihongduc132 made their first contribution in #2124 
 
 Full Changelog : v1.6.7...v1.6.8-rc.25

</details>