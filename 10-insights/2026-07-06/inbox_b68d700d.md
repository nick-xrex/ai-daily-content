---
id: inbox_b68d700d
date: 2026-07-06
source_ref: "[[00-inbox/2026-07-06/2254-gitnexus-releases-release-candidate-v1-6-10-rc-5-6b2a]]"
title: "Release Candidate v1.6.10-rc.5"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.5
source: gitnexus-releases
published_at: 2026-07-06T15:45:54+00:00
fetched_at: 2026-07-07T00:36:54.699540+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus RC 版本 1.6.10-rc.5，內容與 rc.6 相似，整合 CodeBuddy / Qoder coding-agent 和 OpenAI Codex 完整支持。修復 proxy 環境下的安裝問題（onnxruntime-node postinstall）和 embeddings 自我修復，改善 FTS extension 的錯誤診斷，修正 MCP protocol 中 symbol 行號的 0-based/1-based 轉換問題。相比 rc.6 尚缺 Windows FTS 缺依賴診斷功能。"
key_points:
  - "Codex 和 coding-agent 整合功能與 rc.6 一致"
  - "修復 MCP symbol 行號轉換（0-based 儲存 vs 1-based 顯示）"
  - "proxy 環境下的安裝穩定性提升和 embeddings 自我修復"
tags: [gitnexus, codex-integration, mcp-protocol, release-candidate]
topics: [foundation_models.gpt, agents.mcp]
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.5

GitNexus RC 版本 1.6.10-rc.5，內容與 rc.6 相似，整合 CodeBuddy / Qoder coding-agent 和 OpenAI Codex 完整支持。修復 proxy 環境下的安裝問題（onnxruntime-node postinstall）和 embeddings 自我修復，改善 FTS extension 的錯誤診斷，修正 MCP protocol 中 symbol 行號的 0-based/1-based 轉換問題。相比 rc.6 尚缺 Windows FTS 缺依賴診斷功能。

### 重點
- Codex 和 coding-agent 整合功能與 rc.6 一致
- 修復 MCP symbol 行號轉換（0-based 儲存 vs 1-based 顯示）
- proxy 環境下的安裝穩定性提升和 embeddings 自我修復

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.5 \n Target base: 1.6.10 (rc #5 )\n Source commit (main): fbffa96 \n Release commit (versioned tree): 722ab37 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(setup): add CodeBuddy and Qoder coding-agent integrations by @magyargergo in #2368 
 feat: full Codex support — hooks, plugin marketplace, and setup ( #2328 , supersedes #1131 ) by @magyargergo in #2369 
 fix: proxy-blocked installs survive onnxruntime-node postinstall and self-heal embeddings ( #2370 ) by @magyargergo in #2372 
 fix: surface real FTS extension LOAD errors and self-heal broken extension files ( #2374 ) by @magyargergo in #2375 
 fix(lbug/mcp): exact symbol content + 0-based line storage with 1-based MCP display ( #2377 , #2379 ) by @magyargergo in #2380 
 
 Full Changelog : v1.6.9...v1.6.10-rc.5

</details>