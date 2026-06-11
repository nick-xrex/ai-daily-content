---
id: inbox_37d0e9a5
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_37d0e9a5]]"
title: "Release Candidate v1.6.8-rc.14"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.14
source: gitnexus-releases
published_at: 2026-06-10T20:06:23+00:00
fetched_at: 2026-06-11T00:21:04.284599+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 發佈 1.6.8-rc.14 release candidate。與 rc.15、rc.16 包含相同的 changelist，共 13 項提交，包括 VECTOR 索引修復、Docker 資產包含、多分支索引、Java Spring 提取、TS/JS 控制流圖層、blast radius 修復、embeddings 依賴解決等。RC 版本供提前測試，穩定版本維持在 latest dist-tag。"
key_points:
  - "新增多分支索引與分支限定查詢（#2106），支援大規模 repository 的跨分支分析"
  - "修復 VECTOR 索引創建路徑、Docker 資產包含（hooks/, skills/）、embeddings 依賴解決"
  - "新增 Java Spring route annotation 提取和 TS/JS 控制流圖層分析，擴展語言覆蓋"
tags: [gitnexus, code-indexing, vector-db, release-candidate]
topics: []
importance: 2
novelty: 1
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.8-rc.14

GitNexus 發佈 1.6.8-rc.14 release candidate。與 rc.15、rc.16 包含相同的 changelist，共 13 項提交，包括 VECTOR 索引修復、Docker 資產包含、多分支索引、Java Spring 提取、TS/JS 控制流圖層、blast radius 修復、embeddings 依賴解決等。RC 版本供提前測試，穩定版本維持在 latest dist-tag。

### 重點
- 新增多分支索引與分支限定查詢（#2106），支援大規模 repository 的跨分支分析
- 修復 VECTOR 索引創建路徑、Docker 資產包含（hooks/, skills/）、embeddings 依賴解決
- 新增 Java Spring route annotation 提取和 TS/JS 控制流圖層分析，擴展語言覆蓋

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.14)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.8-rc.14

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.14 \n Target base: 1.6.8 (rc #14 )\n Source commit (main): 6424d8b \n Release commit (versioned tree): 10cd6c6 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @buihongduc132 made their first contribution in #2124 
 
 Full Changelog : v1.6.7...v1.6.8-rc.14

</details>