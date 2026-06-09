---
id: inbox_263cbbdc
date: 2026-06-09
source_ref: "[[00-inbox/2026-06-09/2200-gitnexus-releases-release-candidate-v1-6-7-rc-6-87ce]]"
title: "Release Candidate v1.6.7-rc.6"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.6
source: gitnexus-releases
published_at: 2026-06-09T08:13:24+00:00
fetched_at: 2026-06-09T22:06:26.786037+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 釋出第六個發布候選版本 1.6.7-rc.6，引入 taint/PDG 分析基礎設施初版（M0），含 schema、seams、spikes 三大組件。此版本改進 grammar 自動加載機制，防止分析工具在缺少可選文法時崩潰；新增 C++ 繼承鏈成員查詢功能；並優化批量查詢擴展與 FTS 記憶體效能。npm 安裝指令為 npm install gitnexus@rc。"
key_points:
  - "feat(ingestion): M0 taint/PDG substrate 新增 schema、seams、spikes 支援（#2080）"
  - "fix(ingestion): lazy-load 可選 grammar，防止分析在缺少特定文法時崩潰（#2091、#2093）"
  - "feat(cpp): inheritance-lattice member lookup 改進 C++ 依賴解析、fix: batch query enrichment 與 FTS 記憶體最佳化"
tags: [gitnexus, release-candidate, ingestion, cpp, pdk]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.7-rc.6

GitNexus 釋出第六個發布候選版本 1.6.7-rc.6，引入 taint/PDG 分析基礎設施初版（M0），含 schema、seams、spikes 三大組件。此版本改進 grammar 自動加載機制，防止分析工具在缺少可選文法時崩潰；新增 C++ 繼承鏈成員查詢功能；並優化批量查詢擴展與 FTS 記憶體效能。npm 安裝指令為 npm install gitnexus@rc。

### 重點
- feat(ingestion): M0 taint/PDG substrate 新增 schema、seams、spikes 支援（#2080）
- fix(ingestion): lazy-load 可選 grammar，防止分析在缺少特定文法時崩潰（#2091、#2093）
- feat(cpp): inheritance-lattice member lookup 改進 C++ 依賴解析、fix: batch query enrichment 與 FTS 記憶體最佳化

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.6)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.7-rc.6 \n Target base: 1.6.7 (rc #6 )\n Source commit (main): 288b96f \n Release commit (versioned tree): 517d82a \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 chore: Sync Claude plugin manifests with the 1.6.6 release by @Copilot in #2090 
 feat(ingestion): M0 — taint/PDG substrate (schema + seams + spikes) ( #2080 ) by @magyargergo in #2092 
 fix(ingestion): lazy-load optional grammars so analyze never crashes when one is missing ( #2091 , #2093 ) by @magyargergo in #2101 
 feat(cpp): resolve inheritance-lattice member lookup by @azizur100389 in #2077 
 fix: batch query enrichment, bake FTS extension into CLI image, add FTS memory repro by @magyargergo in #2108 
 
 Full Changelog : v1.6.6...v1.6.7-rc.6

</details>