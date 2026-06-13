---
id: inbox_72c9269f
date: 2026-06-12
source_ref: "[[00-inbox/2026-06-12/0336-gitnexus-releases-release-candidate-v1-6-8-rc-20-fe38]]"
title: "Release Candidate v1.6.8-rc.20"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.20
source: gitnexus-releases
published_at: 2026-06-12T06:28:11+00:00
fetched_at: 2026-06-13T03:42:23.409124+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.8-rc.20 包含 15 項改進，與 rc.21 高度重疊但缺少污點分析功能。修復相同的 VECTOR 索引、Docker 打包、MCP 增強問題；新增 Java Spring 路由、多分支索引、TS/JS CFG 層。此 RC 代表架構穩定化階段，在污點分析完成前的中間里程碑。"
key_points:
  - "高度重複的改動集合：核心修復與 rc.21 一致，反映穩定的優先級順序"
  - "差異僅在污點分析：rc.20 缺少 feat(taint) 功能，表明污點分析在 rc.20→rc.21 間完成集成"
  - "漸進式發布模式：多個 RC 版本逐步累積功能，最終合併至穩定版"
tags: [gitnexus, release-candidate, code-analysis]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.20

GitNexus v1.6.8-rc.20 包含 15 項改進，與 rc.21 高度重疊但缺少污點分析功能。修復相同的 VECTOR 索引、Docker 打包、MCP 增強問題；新增 Java Spring 路由、多分支索引、TS/JS CFG 層。此 RC 代表架構穩定化階段，在污點分析完成前的中間里程碑。

### 重點
- 高度重複的改動集合：核心修復與 rc.21 一致，反映穩定的優先級順序
- 差異僅在污點分析：rc.20 缺少 feat(taint) 功能，表明污點分析在 rc.20→rc.21 間完成集成
- 漸進式發布模式：多個 RC 版本逐步累積功能，最終合併至穩定版

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.20)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.20 \n Target base: 1.6.8 (rc #20 )\n Source commit (main): 28f3b99 \n Release commit (versioned tree): 4b63d0c \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @buihongduc132 made their first contribution in #2124 
 
 Full Changelog : v1.6.7...v1.6.8-rc.20

</details>