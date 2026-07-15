---
id: inbox_b93fe880
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-gitnexus-releases-release-candidate-v1-6-10-rc-23-786a]]"
title: "Release Candidate v1.6.10-rc.23"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.23
source: gitnexus-releases
published_at: 2026-07-14T16:28:09+00:00
fetched_at: 2026-07-14T22:05:16.049685+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.23 RC 版本發布。主要新增功能包括 CodeBuddy 和 Qoder coding-agent 集成、完整的 OpenAI Codex 支持（含 hooks 與 plugin marketplace）以及 Icebug 社區引擎原型。同時包含多項重要修復：Windows FTS 依賴診斷、MCP 精確符號內容與 0-based 行號儲存（對應 1-based MCP 顯示）、增量寫回可靠性改善（#2409）、跨平台 CI 測試穩定性優化等。"
key_points:
  - "新增 CodeBuddy 和 Qoder coding-agent 集成，擴展代碼智能功能"
  - "完整 Codex 支持（hooks、plugin marketplace、setup），與 OpenAI 代碼生成工具深度集成"
  - "修復 MCP 符號儲存（0-based line storage vs 1-based display）、Windows FTS 缺失依賴診斷、增量寫回可靠性（#2409）"
tags: [gitnexus, codex-integration, coding-agents, mcp]
topics: [agents.mcp]
importance: 2
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.23

GitNexus v1.6.10-rc.23 RC 版本發布。主要新增功能包括 CodeBuddy 和 Qoder coding-agent 集成、完整的 OpenAI Codex 支持（含 hooks 與 plugin marketplace）以及 Icebug 社區引擎原型。同時包含多項重要修復：Windows FTS 依賴診斷、MCP 精確符號內容與 0-based 行號儲存（對應 1-based MCP 顯示）、增量寫回可靠性改善（#2409）、跨平台 CI 測試穩定性優化等。

### 重點
- 新增 CodeBuddy 和 Qoder coding-agent 集成，擴展代碼智能功能
- 完整 Codex 支持（hooks、plugin marketplace、setup），與 OpenAI 代碼生成工具深度集成
- 修復 MCP 符號儲存（0-based line storage vs 1-based display）、Windows FTS 缺失依賴診斷、增量寫回可靠性（#2409）

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.23)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.23 \n Target base: 1.6.10 (rc #23 )\n Source commit (main): e3136f5 \n Release commit (versioned tree): cc41bd2 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 fix: make large incremental writebacks commit reliably ( #2409 ) by @magyargergo in #2425 
 fix(cli): actionable diagnostics for non-4K page-size buffer manager failures by @vlisitskii in #2424 
 fix(tree-sitter): recover declarations after embedded NUL bytes by @magyargergo in #2430 
 fix(web): use repo path identity in switcher by @koriyoshi2041 in #2420 
 fix: stop Napi::Error SIGABRT on analyze — index C++ type lookups, terminate workers only at JS-safe points ( #2432 ) by @magyargergo in #2436 
 ci: update setup composites to setup-node v6 by @100yenadmin in #2451 
 
 New Contributors 
 
 @vlisitskii made their first contribution in #2424 
 @100yenadmin made their first contribution in #2451 
 
 Full Changelog : v1.6.9...v1.6.10-rc.23

</details>