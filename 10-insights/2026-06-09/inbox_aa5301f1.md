---
id: inbox_aa5301f1
date: 2026-06-09
source_ref: "[[00-inbox/2026-06-09/2200-gitnexus-releases-release-candidate-v1-6-7-rc-11-f593]]"
title: "Release Candidate v1.6.7-rc.11"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.11
source: gitnexus-releases
published_at: 2026-06-09T19:09:56+00:00
fetched_at: 2026-06-09T22:05:17.501041+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.7-rc.11 候選版本發布。變更清單與 rc.12 幾乎相同，包括 PDG 基礎設施、惰性語法載入、C++ 繼承鏈解析、FTS 優化、Kotlin 工具鏈優化、CLI 卸載命令等。相比 rc.12，本版本尚未包含 MCP list_repos 分頁優化和部分 CI 修復。本版本為預發布測試版。"
key_points:
  - "PDG 子圖基礎設施 M0、惰性語法載入、FTS 記憶體優化等核心特性已包含"
  - "tree-sitter 預編譯支援 npm 打包（缺 arm64 CI 調整）"
  - "相比 rc.12 缺少 MCP 分頁優化和最新 CI 修復"
tags: [gitnexus, code-analysis, release-candidate]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.7-rc.11

GitNexus v1.6.7-rc.11 候選版本發布。變更清單與 rc.12 幾乎相同，包括 PDG 基礎設施、惰性語法載入、C++ 繼承鏈解析、FTS 優化、Kotlin 工具鏈優化、CLI 卸載命令等。相比 rc.12，本版本尚未包含 MCP list_repos 分頁優化和部分 CI 修復。本版本為預發布測試版。

### 重點
- PDG 子圖基礎設施 M0、惰性語法載入、FTS 記憶體優化等核心特性已包含
- tree-sitter 預編譯支援 npm 打包（缺 arm64 CI 調整）
- 相比 rc.12 缺少 MCP 分頁優化和最新 CI 修復

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.11)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.7-rc.11 \n Target base: 1.6.7 (rc #11 )\n Source commit (main): bd90d5b \n Release commit (versioned tree): 66b235f \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 chore: Sync Claude plugin manifests with the 1.6.6 release by @Copilot in #2090 
 feat(ingestion): M0 — taint/PDG substrate (schema + seams + spikes) ( #2080 ) by @magyargergo in #2092 
 fix(ingestion): lazy-load optional grammars so analyze never crashes when one is missing ( #2091 , #2093 ) by @magyargergo in #2101 
 feat(cpp): resolve inheritance-lattice member lookup by @azizur100389 in #2077 
 fix: batch query enrichment, bake FTS extension into CLI image, add FTS memory repro by @magyargergo in #2108 
 fix(install): graceful Kotlin optional-grammar install + accurate toolchain docs by @magyargergo in #2110 
 feat(cli): add gitnexus uninstall to reverse setup ( #2060 ) by @NilotpalK in #2062 
 feat(install): toolchain-free tree-sitter via vendored prebuilds by @magyargergo in #2113 
 fix(ci): drop broken -t 22 from prebuildify in build-tree-sitter-prebuilds by @magyargergo in #2121 
 fix(ci): green the tree-sitter prebuild matrix (npm-bundled prebuilds + arm64 runtime) by @magyargergo in #2122 
 
 Full Changelog : v1.6.6...v1.6.7-rc.11

</details>