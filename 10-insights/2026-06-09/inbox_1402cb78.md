---
id: inbox_1402cb78
date: 2026-06-09
source_ref: "[[00-inbox/2026-06-09/2200-gitnexus-releases-release-candidate-v1-6-7-rc-13-003e]]"
title: "Release Candidate v1.6.7-rc.13"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.13
source: gitnexus-releases
published_at: 2026-06-09T20:17:22+00:00
fetched_at: 2026-06-09T22:04:18.471412+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 1.6.7-rc.13 為自動化 release candidate 構建，基於 main 分支。RC 版本供早期測試使用，內容與穩定版 1.6.7 相同，包括 toolchain-free tree-sitter、uninstall command、MCP pagination 等核心功能。穩定版本仍發布在 latest dist-tag。"
key_points:
  - "版本 1.6.7-rc.13：automated RC build from main"
  - "RC 版本用於早期測試，穩定版本發布在 latest dist-tag"
  - "功能同 1.6.7 穩定版"
tags: [gitnexus, release-candidate]
topics: [agents.mcp]
importance: 2
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.7-rc.13

GitNexus 1.6.7-rc.13 為自動化 release candidate 構建，基於 main 分支。RC 版本供早期測試使用，內容與穩定版 1.6.7 相同，包括 toolchain-free tree-sitter、uninstall command、MCP pagination 等核心功能。穩定版本仍發布在 latest dist-tag。

### 重點
- 版本 1.6.7-rc.13：automated RC build from main
- RC 版本用於早期測試，穩定版本發布在 latest dist-tag
- 功能同 1.6.7 穩定版

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.13)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.7-rc.13 \n Target base: 1.6.7 (rc #13 )\n Source commit (main): d0452d2 \n Release commit (versioned tree): 022c25a \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 feat(mcp): paginate list_repos to avoid client token truncation ( #2119 ) by @magyargergo in #2120 
 fix(ci): make the prebuild PR push re-run-safe (--force-with-lease → --force) by @magyargergo in #2123 
 chore(vendor): tree-sitter prebuilds (tree-sitter-c,tree-sitter-dart,tree-sitter-proto,tree-sitter-kotlin,tree-sitter-swift) by @gitnexus-release-bot[bot] in #2125 
 
 New Contributors 
 
 @gitnexus-release-bot[bot] made their first contribution in #2125 
 
 Full Changelog : v1.6.6...v1.6.7-rc.13

</details>