---
id: inbox_81be145c
date: 2026-07-07
source_ref: "[[00-inbox/.../inbox_81be145c]]"
title: "Release Candidate v1.6.10-rc.7"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.7
source: gitnexus-releases
published_at: 2026-07-07T05:24:19+00:00
fetched_at: 2026-07-08T00:59:09.652130+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 發布 RC 版本 v1.6.10-rc.7（目標穩定版 1.6.10）。主要新增完整的 Codex 支援（hooks、plugin marketplace、setup）與 CodeBuddy / Qoder 編碼 agent 整合。修復涵蓋：proxy 阻擋環境下 onnxruntime-node postinstall 的自我修復、FTS 擴展 LOAD 錯誤診斷與自動恢復、lbug/mcp 的 0-based 內部儲存與 1-based MCP 顯示轉換、Windows FTS 缺少依賴偵測（Phase 1）。展現「self-healing」設計理念：錯誤被捕捉、診斷並自動恢復，減少手工介入。RC 版本用於早期測試。"
key_points:
  - "完整 Codex 支援上線（hooks、plugin marketplace、setup），新增 CodeBuddy / Qoder 編碼 agent 整合"
  - "自我修復機制：proxy 阻擋下 onnxruntime-node postinstall 能倖存並恢復、FTS 擴展 LOAD 失敗能自動診斷與修復"
  - "MCP 整合改進：lbug/mcp 精確符號內容管理、0-based/1-based line number 轉換層、自訂 HTTP embedding 端點失敗報告"
tags: [gitnexus, codex-integration, self-healing, mcp-support, release-candidate]
topics: [agents.mcp]
importance: 3
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.7

GitNexus 發布 RC 版本 v1.6.10-rc.7（目標穩定版 1.6.10）。主要新增完整的 Codex 支援（hooks、plugin marketplace、setup）與 CodeBuddy / Qoder 編碼 agent 整合。修復涵蓋：proxy 阻擋環境下 onnxruntime-node postinstall 的自我修復、FTS 擴展 LOAD 錯誤診斷與自動恢復、lbug/mcp 的 0-based 內部儲存與 1-based MCP 顯示轉換、Windows FTS 缺少依賴偵測（Phase 1）。展現「self-healing」設計理念：錯誤被捕捉、診斷並自動恢復，減少手工介入。RC 版本用於早期測試。

### 重點
- 完整 Codex 支援上線（hooks、plugin marketplace、setup），新增 CodeBuddy / Qoder 編碼 agent 整合
- 自我修復機制：proxy 阻擋下 onnxruntime-node postinstall 能倖存並恢復、FTS 擴展 LOAD 失敗能自動診斷與修復
- MCP 整合改進：lbug/mcp 精確符號內容管理、0-based/1-based line number 轉換層、自訂 HTTP embedding 端點失敗報告

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.7)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.10-rc.7

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.7 \n Target base: 1.6.10 (rc #7 )\n Source commit (main): b98f6e4 \n Release commit (versioned tree): c1e6983 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(setup): add CodeBuddy and Qoder coding-agent integrations by @magyargergo in #2368 
 feat: full Codex support — hooks, plugin marketplace, and setup ( #2328 , supersedes #1131 ) by @magyargergo in #2369 
 fix: proxy-blocked installs survive onnxruntime-node postinstall and self-heal embeddings ( #2370 ) by @magyargergo in #2372 
 fix: surface real FTS extension LOAD errors and self-heal broken extension files ( #2374 ) by @magyargergo in #2375 
 fix(lbug/mcp): exact symbol content + 0-based line storage with 1-based MCP display ( #2377 , #2379 ) by @magyargergo in #2380 
 fix(fts): diagnose Windows FTS missing-dependency load failures ( #2374 , Phase 1) by @magyargergo in #2383 
 fix: report custom HTTP embedding endpoint failures instead of huggingface download errors ( #2385 ) by @magyargergo in #2386 
 fix(lbug): recognize Windows missing-shadow error so serve repo-switch recovers ( #2382 ) by @magyargergo in #2387 
 
 Full Changelog : v1.6.9...v1.6.10-rc.7

</details>