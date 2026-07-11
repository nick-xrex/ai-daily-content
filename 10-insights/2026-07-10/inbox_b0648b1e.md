---
id: inbox_b0648b1e
date: 2026-07-10
source_ref: "[[00-inbox/.../inbox_b0648b1e]]"
title: "Release Candidate v1.6.10-rc.13"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.13
source: gitnexus-releases
published_at: 2026-07-10T05:30:15+00:00
fetched_at: 2026-07-11T01:54:18.525869+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.13（Release Candidate）是第一個發布的 RC 版本，涵蓋 Codex 整合、CodeBuddy/Qoder 編碼 agent、Proxy-blocked 環境 self-heal、FTS extension 診斷、MCP symbol content 精確定位、Windows FTS 依賴檢查、HTTP embedding endpoint 錯誤報告、FastAPI 路由常數解析、跨平台 timeout 修復、MCP query hint DB lock 檢測等改進。相比後續 rc.14 和 rc.15，缺少大型增量 writeback 可靠性改進（#2425）和 CLI 診斷改進（#2424）。"
key_points:
  - "Codex 支援、CodeBuddy/Qoder agent 整合、MCP DB lock hint 等核心改進已包含"
  - "Proxy/FTS/embedding endpoint 自癒機制、symbol 精確定位已實裝"
  - "後續版本（rc.14/rc.15）新增增量 writeback 可靠性與 CLI 診斷改進"
tags: [gitnexus, release-candidate, codex]
topics: [agents.mcp]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.13

GitNexus v1.6.10-rc.13（Release Candidate）是第一個發布的 RC 版本，涵蓋 Codex 整合、CodeBuddy/Qoder 編碼 agent、Proxy-blocked 環境 self-heal、FTS extension 診斷、MCP symbol content 精確定位、Windows FTS 依賴檢查、HTTP embedding endpoint 錯誤報告、FastAPI 路由常數解析、跨平台 timeout 修復、MCP query hint DB lock 檢測等改進。相比後續 rc.14 和 rc.15，缺少大型增量 writeback 可靠性改進（#2425）和 CLI 診斷改進（#2424）。

### 重點
- Codex 支援、CodeBuddy/Qoder agent 整合、MCP DB lock hint 等核心改進已包含
- Proxy/FTS/embedding endpoint 自癒機制、symbol 精確定位已實裝
- 後續版本（rc.14/rc.15）新增增量 writeback 可靠性與 CLI 診斷改進

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.13)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.10-rc.13

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.13 \n Target base: 1.6.10 (rc #13 )\n Source commit (main): ebedfe0 \n Release commit (versioned tree): 06284e5 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 fix: surface incremental dirty state diagnostics by @koriyoshi2041 in #2410 
 
 Full Changelog : v1.6.9...v1.6.10-rc.13

</details>