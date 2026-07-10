---
id: inbox_a11b0e09
date: 2026-07-09
source_ref: "[[00-inbox/2026-07-09/2207-gitnexus-releases-release-candidate-v1-6-10-rc-11-da4a]]"
title: "Release Candidate v1.6.10-rc.11"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.11
source: gitnexus-releases
published_at: 2026-07-09T07:04:22+00:00
fetched_at: 2026-07-10T00:16:22.078823+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.11 是自動化發布候選構建。本版本新增 CodeBuddy 和 Qoder 編程代理整合，以及完整的 Codex 支援（hooks、plugin marketplace、setup）。同時包含多項穩定性修復，針對 Windows 平台相容性、FTS extension 自癒、proxy-blocked 安裝恢復、MCP 符號編號一致性等進行改善。修復範圍包括 FTS 依賴診斷、missing-shadow 錯誤識別、FastAPI routing 解析等。此版本於 rc.10 發布後約一小時推出。"
key_points:
  - "新增 CodeBuddy、Qoder 編程代理整合及完整 Codex 支援（hooks、plugin marketplace、setup）"
  - "Windows 穩定性修復：FTS 依賴診斷、missing-shadow 錯誤識別、跨平台 CI 超時優化"
  - "自癒與相容性改善：proxy-blocked 安裝恢復、embeddings 自癒、FastAPI route path 解析、MCP 行編號正確性（0-based vs 1-based）"
tags: [gitnexus, release-candidate, coding-agents, windows-compat, self-healing]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.11

GitNexus v1.6.10-rc.11 是自動化發布候選構建。本版本新增 CodeBuddy 和 Qoder 編程代理整合，以及完整的 Codex 支援（hooks、plugin marketplace、setup）。同時包含多項穩定性修復，針對 Windows 平台相容性、FTS extension 自癒、proxy-blocked 安裝恢復、MCP 符號編號一致性等進行改善。修復範圍包括 FTS 依賴診斷、missing-shadow 錯誤識別、FastAPI routing 解析等。此版本於 rc.10 發布後約一小時推出。

### 重點
- 新增 CodeBuddy、Qoder 編程代理整合及完整 Codex 支援（hooks、plugin marketplace、setup）
- Windows 穩定性修復：FTS 依賴診斷、missing-shadow 錯誤識別、跨平台 CI 超時優化
- 自癒與相容性改善：proxy-blocked 安裝恢復、embeddings 自癒、FastAPI route path 解析、MCP 行編號正確性（0-based vs 1-based）

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.11)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.11 \n Target base: 1.6.10 (rc #11 )\n Source commit (main): 3e38cd0 \n Release commit (versioned tree): b10341b \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 Full Changelog : v1.6.9...v1.6.10-rc.11

</details>