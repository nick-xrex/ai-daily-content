---
id: inbox_6fc120a3
date: 2026-06-09
source_ref: "[[00-inbox/2026-06-09/2200-gitnexus-releases-release-candidate-v1-6-7-rc-5-6247]]"
title: "Release Candidate v1.6.7-rc.5"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.5
source: gitnexus-releases
published_at: 2026-06-09T06:07:57+00:00
fetched_at: 2026-06-09T22:06:26.792361+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 釋出第五個發布候選版本 1.6.7-rc.5，是 1.6.6 至 1.6.7 開發過程中的中間版本。此版本包含 taint/PDG 分析基礎設施初版、自動 grammar 加載修復、C++ 繼承鏈成員查詢功能。與後續 rc.6 相比，該版本未納入 batch query enrichment 與 FTS 相關優化。npm 安裝指令為 npm install gitnexus@rc。"
key_points:
  - "feat(ingestion): M0 taint/PDG substrate 提供初始分析框架（#2080）"
  - "fix(ingestion): lazy-load 可選 grammar 防止缺失文法導致分析崩潰（#2091、#2093）"
  - "feat(cpp): inheritance-lattice member lookup 改進 C++ 依賴解析"
tags: [gitnexus, release-candidate, ingestion, cpp]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.7-rc.5

GitNexus 釋出第五個發布候選版本 1.6.7-rc.5，是 1.6.6 至 1.6.7 開發過程中的中間版本。此版本包含 taint/PDG 分析基礎設施初版、自動 grammar 加載修復、C++ 繼承鏈成員查詢功能。與後續 rc.6 相比，該版本未納入 batch query enrichment 與 FTS 相關優化。npm 安裝指令為 npm install gitnexus@rc。

### 重點
- feat(ingestion): M0 taint/PDG substrate 提供初始分析框架（#2080）
- fix(ingestion): lazy-load 可選 grammar 防止缺失文法導致分析崩潰（#2091、#2093）
- feat(cpp): inheritance-lattice member lookup 改進 C++ 依賴解析

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.7-rc.5 \n Target base: 1.6.7 (rc #5 )\n Source commit (main): 3a4247e \n Release commit (versioned tree): aacece9 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 chore: Sync Claude plugin manifests with the 1.6.6 release by @Copilot in #2090 
 feat(ingestion): M0 — taint/PDG substrate (schema + seams + spikes) ( #2080 ) by @magyargergo in #2092 
 fix(ingestion): lazy-load optional grammars so analyze never crashes when one is missing ( #2091 , #2093 ) by @magyargergo in #2101 
 feat(cpp): resolve inheritance-lattice member lookup by @azizur100389 in #2077 
 
 Full Changelog : v1.6.6...v1.6.7-rc.5

</details>