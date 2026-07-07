---
id: inbox_1d1b9f45
date: 2026-07-06
source_ref: "[[00-inbox/2026-07-06/2254-gitnexus-releases-release-candidate-v1-6-10-rc-4-eab8]]"
title: "Release Candidate v1.6.10-rc.4"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.4
source: gitnexus-releases
published_at: 2026-07-06T05:59:37+00:00
fetched_at: 2026-07-07T00:36:54.703797+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus RC 版本 1.6.10-rc.4，相比 rc.5 更早的迭代版本，仍包含 CodeBuddy / Qoder coding-agent 和 OpenAI Codex 完整支持的功能。修復 proxy 環境下的安裝問題、FTS extension 錯誤診斷、MCP symbol 內容儲存等。相比後續 RC 版本缺少 Windows FTS 診斷和其他細節優化。"
key_points:
  - "Codex 整合支持和 coding-agent 多選能力基本具備"
  - "proxy 環境安裝穩定性修復和 FTS 錯誤診斷"
  - "MCP symbol 內容精確性改進（0-based 儲存）"
tags: [gitnexus, codex-integration, release-candidate]
topics: [foundation_models.gpt, agents.mcp]
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.4

GitNexus RC 版本 1.6.10-rc.4，相比 rc.5 更早的迭代版本，仍包含 CodeBuddy / Qoder coding-agent 和 OpenAI Codex 完整支持的功能。修復 proxy 環境下的安裝問題、FTS extension 錯誤診斷、MCP symbol 內容儲存等。相比後續 RC 版本缺少 Windows FTS 診斷和其他細節優化。

### 重點
- Codex 整合支持和 coding-agent 多選能力基本具備
- proxy 環境安裝穩定性修復和 FTS 錯誤診斷
- MCP symbol 內容精確性改進（0-based 儲存）

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.4 \n Target base: 1.6.10 (rc #4 )\n Source commit (main): 177bbc8 \n Release commit (versioned tree): 3e4985a \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(setup): add CodeBuddy and Qoder coding-agent integrations by @magyargergo in #2368 
 feat: full Codex support — hooks, plugin marketplace, and setup ( #2328 , supersedes #1131 ) by @magyargergo in #2369 
 fix: proxy-blocked installs survive onnxruntime-node postinstall and self-heal embeddings ( #2370 ) by @magyargergo in #2372 
 fix: surface real FTS extension LOAD errors and self-heal broken extension files ( #2374 ) by @magyargergo in #2375 
 
 Full Changelog : v1.6.9...v1.6.10-rc.4

</details>