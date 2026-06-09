---
id: inbox_4b4d678d
date: 2026-06-09
source_ref: "[[00-inbox/2026-06-09/2200-gitnexus-releases-release-candidate-v1-6-7-rc-8-1cef]]"
title: "Release Candidate v1.6.7-rc.8"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.8
source: gitnexus-releases
published_at: 2026-06-09T10:08:32+00:00
fetched_at: 2026-06-09T22:05:17.505810+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.7-rc.8 候選版本發布。包含 PDG 基礎設施、惰性語法載入、C++ 繼承鏈解析、FTS 優化、Kotlin 工具鏈優化等特性。相比 rc.7，新增 CLI 卸載命令和 tree-sitter CI 最佳化（green the prebuild matrix）。本版本為預發布測試版。"
key_points:
  - "PDG 子圖基礎設施 M0、可選語法惰性載入、C++ 繼承鏈解析等已實裝"
  - "新增 gitnexus uninstall 反向安裝命令"
  - "tree-sitter CI 改進使預編譯矩陣通過"
tags: [gitnexus, code-analysis, release-candidate]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.7-rc.8

GitNexus v1.6.7-rc.8 候選版本發布。包含 PDG 基礎設施、惰性語法載入、C++ 繼承鏈解析、FTS 優化、Kotlin 工具鏈優化等特性。相比 rc.7，新增 CLI 卸載命令和 tree-sitter CI 最佳化（green the prebuild matrix）。本版本為預發布測試版。

### 重點
- PDG 子圖基礎設施 M0、可選語法惰性載入、C++ 繼承鏈解析等已實裝
- 新增 gitnexus uninstall 反向安裝命令
- tree-sitter CI 改進使預編譯矩陣通過

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.8)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.7-rc.8 \n Target base: 1.6.7 (rc #8 )\n Source commit (main): 1716bf7 \n Release commit (versioned tree): 661029f \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 chore: Sync Claude plugin manifests with the 1.6.6 release by @Copilot in #2090 
 feat(ingestion): M0 — taint/PDG substrate (schema + seams + spikes) ( #2080 ) by @magyargergo in #2092 
 fix(ingestion): lazy-load optional grammars so analyze never crashes when one is missing ( #2091 , #2093 ) by @magyargergo in #2101 
 feat(cpp): resolve inheritance-lattice member lookup by @azizur100389 in #2077 
 fix: batch query enrichment, bake FTS extension into CLI image, add FTS memory repro by @magyargergo in #2108 
 fix(install): graceful Kotlin optional-grammar install + accurate toolchain docs by @magyargergo in #2110 
 feat(cli): add gitnexus uninstall to reverse setup ( #2060 ) by @NilotpalK in #2062 
 
 Full Changelog : v1.6.6...v1.6.7-rc.8

</details>