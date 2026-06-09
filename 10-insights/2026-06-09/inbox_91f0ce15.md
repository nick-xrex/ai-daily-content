---
id: inbox_91f0ce15
date: 2026-06-09
source_ref: "[[00-inbox/2026-06-09/2200-gitnexus-releases-release-candidate-v1-6-7-rc-7-6dab]]"
title: "Release Candidate v1.6.7-rc.7"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.7
source: gitnexus-releases
published_at: 2026-06-09T08:46:54+00:00
fetched_at: 2026-06-09T22:05:17.507079+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.7-rc.7 候選版本發布。包含 Taint/PDG 子圖基礎設施 M0 實現、可選語法惰性載入、C++ 繼承鏈成員查詢解析、FTS 擴展集成、Kotlin 工具鏈優化等核心特性。這是最早發布的候選版本，後續版本 (rc.8–rc.12) 逐步新增 CLI 卸載命令、tree-sitter 預編譯、MCP 分頁等改進。本版本為預發布測試版。"
key_points:
  - "Taint/PDG 子圖基礎設施 M0——schema + seams + spikes 的初始實現"
  - "可選語法惰性載入，防止分析器在缺失語法時崩潰；FTS 擴展集成"
  - "C++ 繼承鏈成員查詢解析；Kotlin 工具鏈優化"
tags: [gitnexus, code-analysis, release-candidate]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.7-rc.7

GitNexus v1.6.7-rc.7 候選版本發布。包含 Taint/PDG 子圖基礎設施 M0 實現、可選語法惰性載入、C++ 繼承鏈成員查詢解析、FTS 擴展集成、Kotlin 工具鏈優化等核心特性。這是最早發布的候選版本，後續版本 (rc.8–rc.12) 逐步新增 CLI 卸載命令、tree-sitter 預編譯、MCP 分頁等改進。本版本為預發布測試版。

### 重點
- Taint/PDG 子圖基礎設施 M0——schema + seams + spikes 的初始實現
- 可選語法惰性載入，防止分析器在缺失語法時崩潰；FTS 擴展集成
- C++ 繼承鏈成員查詢解析；Kotlin 工具鏈優化

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.7)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.7-rc.7 \n Target base: 1.6.7 (rc #7 )\n Source commit (main): f115166 \n Release commit (versioned tree): 54e4573 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 chore: Sync Claude plugin manifests with the 1.6.6 release by @Copilot in #2090 
 feat(ingestion): M0 — taint/PDG substrate (schema + seams + spikes) ( #2080 ) by @magyargergo in #2092 
 fix(ingestion): lazy-load optional grammars so analyze never crashes when one is missing ( #2091 , #2093 ) by @magyargergo in #2101 
 feat(cpp): resolve inheritance-lattice member lookup by @azizur100389 in #2077 
 fix: batch query enrichment, bake FTS extension into CLI image, add FTS memory repro by @magyargergo in #2108 
 fix(install): graceful Kotlin optional-grammar install + accurate toolchain docs by @magyargergo in #2110 
 
 Full Changelog : v1.6.6...v1.6.7-rc.7

</details>