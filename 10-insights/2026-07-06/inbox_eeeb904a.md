---
id: inbox_eeeb904a
date: 2026-07-06
source_ref: "[[00-inbox/2026-07-06/2254-gitnexus-releases-release-candidate-v1-6-10-rc-6-f780]]"
title: "Release Candidate v1.6.10-rc.6"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.6
source: gitnexus-releases
published_at: 2026-07-06T20:49:17+00:00
fetched_at: 2026-07-07T00:36:54.453833+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 發布 RC 版本 1.6.10-rc.6，此版本整合了 CodeBuddy 和 Qoder 兩種 coding-agent，新增 OpenAI Codex 完整支持（含 hooks、plugin marketplace、setup 機制）。修復了在 proxy 封鎖環境下 onnxruntime-node postinstall 和 embeddings 自我修復的問題，改善了 FTS extension 的錯誤診斷能力，修正了 MCP protocol 中 symbol 內容儲存時 0-based 與 1-based 行號的轉換差異，並新增了 Windows 平台 FTS 依賴缺失的診斷功能。"
key_points:
  - "OpenAI Codex 完整支持加入 plugin marketplace 和 setup hooks，顯著擴展編輯器 AI 編碼能力"
  - "整合 CodeBuddy 和 Qoder 等多種 coding-agent，讓用戶可選用不同 AI 編碼助手"
  - "修復 MCP protocol 中 symbol 的 0-based 行號儲存與 1-based MCP 顯示的差異"
tags: [gitnexus, codex-integration, mcp-protocol, coding-agents, release-candidate]
topics: [foundation_models.gpt, agents.mcp]
importance: 3
novelty: 3
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.6

GitNexus 發布 RC 版本 1.6.10-rc.6，此版本整合了 CodeBuddy 和 Qoder 兩種 coding-agent，新增 OpenAI Codex 完整支持（含 hooks、plugin marketplace、setup 機制）。修復了在 proxy 封鎖環境下 onnxruntime-node postinstall 和 embeddings 自我修復的問題，改善了 FTS extension 的錯誤診斷能力，修正了 MCP protocol 中 symbol 內容儲存時 0-based 與 1-based 行號的轉換差異，並新增了 Windows 平台 FTS 依賴缺失的診斷功能。

### 重點
- OpenAI Codex 完整支持加入 plugin marketplace 和 setup hooks，顯著擴展編輯器 AI 編碼能力
- 整合 CodeBuddy 和 Qoder 等多種 coding-agent，讓用戶可選用不同 AI 編碼助手
- 修復 MCP protocol 中 symbol 的 0-based 行號儲存與 1-based MCP 顯示的差異

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.6)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.6 \n Target base: 1.6.10 (rc #6 )\n Source commit (main): 76a1c90 \n Release commit (versioned tree): 1e3dad7 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(setup): add CodeBuddy and Qoder coding-agent integrations by @magyargergo in #2368 
 feat: full Codex support — hooks, plugin marketplace, and setup ( #2328 , supersedes #1131 ) by @magyargergo in #2369 
 fix: proxy-blocked installs survive onnxruntime-node postinstall and self-heal embeddings ( #2370 ) by @magyargergo in #2372 
 fix: surface real FTS extension LOAD errors and self-heal broken extension files ( #2374 ) by @magyargergo in #2375 
 fix(lbug/mcp): exact symbol content + 0-based line storage with 1-based MCP display ( #2377 , #2379 ) by @magyargergo in #2380 
 fix(fts): diagnose Windows FTS missing-dependency load failures ( #2374 , Phase 1) by @magyargergo in #2383 
 
 Full Changelog : v1.6.9...v1.6.10-rc.6

</details>