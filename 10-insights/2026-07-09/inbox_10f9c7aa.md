---
id: inbox_10f9c7aa
date: 2026-07-09
source_ref: "[[00-inbox/2026-07-09/2207-gitnexus-releases-release-candidate-v1-6-10-rc-12-f791]]"
title: "Release Candidate v1.6.10-rc.12"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.12
source: gitnexus-releases
published_at: 2026-07-09T09:13:53+00:00
fetched_at: 2026-07-10T00:16:22.071044+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.12 發布候選版本新增編程代理整合功能。具體包括 CodeBuddy 和 Qoder 編程代理，以及完整的 Codex 支援（hooks、plugin marketplace、setup）。本次 RC 包含多項穩定性修復，重點針對 Windows 平台相容性問題。修復內容涵蓋 FTS extension 自癒機制、0-based/1-based 行編號轉換、proxy-blocked 安裝恢復、HTTP embedding 端點錯誤報告等。Web UI 也改進了 repository dropdown 搜尋功能。CI 流程進一步優化了 Windows 跨平台超時問題。"
key_points:
  - "新增 CodeBuddy、Qoder 編程代理整合與完整 Codex 支援（hooks、plugin marketplace、setup）"
  - "Windows 平台穩定性改善：FTS 依賴診斷、missing-shadow 錯誤識別、跨平台 CI 超時修復"
  - "自癒機制增強：proxy-blocked 安裝恢復、embeddings 自癒、FTS extension 損壞檔案修復，以及 MCP 符號內容精確性與行編號一致性（0-based 存儲 vs 1-based 顯示）"
tags: [gitnexus, release-candidate, coding-agents, windows-compat, self-healing]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.12

GitNexus v1.6.10-rc.12 發布候選版本新增編程代理整合功能。具體包括 CodeBuddy 和 Qoder 編程代理，以及完整的 Codex 支援（hooks、plugin marketplace、setup）。本次 RC 包含多項穩定性修復，重點針對 Windows 平台相容性問題。修復內容涵蓋 FTS extension 自癒機制、0-based/1-based 行編號轉換、proxy-blocked 安裝恢復、HTTP embedding 端點錯誤報告等。Web UI 也改進了 repository dropdown 搜尋功能。CI 流程進一步優化了 Windows 跨平台超時問題。

### 重點
- 新增 CodeBuddy、Qoder 編程代理整合與完整 Codex 支援（hooks、plugin marketplace、setup）
- Windows 平台穩定性改善：FTS 依賴診斷、missing-shadow 錯誤識別、跨平台 CI 超時修復
- 自癒機制增強：proxy-blocked 安裝恢復、embeddings 自癒、FTS extension 損壞檔案修復，以及 MCP 符號內容精確性與行編號一致性（0-based 存儲 vs 1-based 顯示）

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.12)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.12 \n Target base: 1.6.10 (rc #12 )\n Source commit (main): 950c0a7 \n Release commit (versioned tree): e056e71 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 fix: resolve imported/composed FastAPI route path constants ( #2391 ) by @magyargergo in #2393 
 fix(ci): shard platform-sensitive matrix + spawn built CLI to fix Windows cross-platform timeout by @magyargergo in #2394 
 fix(hook): emit MCP query hint when server owns DB lock ( #2396 ) by @magyargergo in #2397 
 feat: gate Icebug community engine prototype by @azizur100389 in #2376 
 fix(web): improve repository dropdown search by @evander-wang in #2381 
 
 Full Changelog : v1.6.9...v1.6.10-rc.12

</details>