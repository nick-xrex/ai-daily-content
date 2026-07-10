---
id: inbox_884488cf
date: 2026-07-09
source_ref: "[[00-inbox/2026-07-09/2207-gitnexus-releases-release-candidate-v1-6-10-rc-10-2a5c]]"
title: "Release Candidate v1.6.10-rc.10"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.10
source: gitnexus-releases
published_at: 2026-07-09T06:11:44+00:00
fetched_at: 2026-07-10T00:16:22.083599+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.10 是自動化發布候選構建。本版本新增 CodeBuddy 和 Qoder 編程代理整合，以及完整的 Codex 支援（hooks、plugin marketplace、setup）。重點修復針對 Windows 平台相容性進行專項改善。包含 FTS extension 依賴診斷、missing-shadow 錯誤識別、embedding 自癒機制、FastAPI route path 解析、以及 MCP 協議層面的符號精確度與行編號映射等修復。跨平台 CI 流程也得到了超時優化。"
key_points:
  - "新增 CodeBuddy、Qoder 編程代理整合及完整 Codex 支援（hooks、plugin marketplace、setup）"
  - "Windows 相容性專項修復：FTS 依賴缺失診斷、missing-shadow 錯誤識別、CI 跨平台超時優化"
  - "自癒與正確性增強：proxy-blocked 安裝恢復、embeddings 自癒、extension 檔案修復、FastAPI routing 解析、MCP 符號精確度與行編號映射（0-based vs 1-based）"
tags: [gitnexus, release-candidate, coding-agents, windows-compat, self-healing]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.10

GitNexus v1.6.10-rc.10 是自動化發布候選構建。本版本新增 CodeBuddy 和 Qoder 編程代理整合，以及完整的 Codex 支援（hooks、plugin marketplace、setup）。重點修復針對 Windows 平台相容性進行專項改善。包含 FTS extension 依賴診斷、missing-shadow 錯誤識別、embedding 自癒機制、FastAPI route path 解析、以及 MCP 協議層面的符號精確度與行編號映射等修復。跨平台 CI 流程也得到了超時優化。

### 重點
- 新增 CodeBuddy、Qoder 編程代理整合及完整 Codex 支援（hooks、plugin marketplace、setup）
- Windows 相容性專項修復：FTS 依賴缺失診斷、missing-shadow 錯誤識別、CI 跨平台超時優化
- 自癒與正確性增強：proxy-blocked 安裝恢復、embeddings 自癒、extension 檔案修復、FastAPI routing 解析、MCP 符號精確度與行編號映射（0-based vs 1-based）

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.10)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.10 \n Target base: 1.6.10 (rc #10 )\n Source commit (main): d287f98 \n Release commit (versioned tree): 8333e62 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 Full Changelog : v1.6.9...v1.6.10-rc.10

</details>