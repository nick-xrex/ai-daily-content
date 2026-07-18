---
id: inbox_c5455f62
date: 2026-07-17
source_ref: "[[00-inbox/.../inbox_c5455f62]]"
title: "Release Candidate v1.6.10-rc.45"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.45
source: gitnexus-releases
published_at: 2026-07-17T16:55:28+00:00
fetched_at: 2026-07-18T01:43:24.330744+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.45 於 2026 年 7 月 17 日 16:55 UTC 發佈，是 RC 版本系列的最後一個候選版本。聚焦 MCP 確定性政策系列（失敗封閉只讀、倉庫白名單、遠端 Bearer 認證、確定性預算）、CodeBuddy 和 Qoder 編碼代理整合、完整 Codex 支持（hooks、插件市場、安裝流程）、embeddings 和 FTS 自癒機制、Windows 平台穩定性加固（FTS 診斷、Napi SIGABRT 修復、符號索引行號映射）。快取/CLI/嵌入管道系列提供 HTTP 可恢復性、批量插入重試安全、解析檔案邊界控制、文本承載回退、樹 sitter NUL 位元組恢復、呼叫引用流程解析。作為預發佈版本供早期測試。"
key_points:
  - "MCP 確定性政策系列完整落地：失敗封閉只讀模式、倉庫白名單強制、遠端綁定 Bearer 認證、確定性回應預算"
  - "多層次自癒機制：embeddings 安裝恢復、FTS 擴展自癒、嵌入管道復原"
  - "Windows 平台加固：FTS 缺依賴診斷、Napi SIGABRT 修復、符號索引 0-based/1-based 映射、呼叫引用流程解析"
tags: [gitnexus, codex-support, coding-agents, mcp-policy, determinism, self-heal, windows-stability, scope-resolution]
topics: [agents.mcp]
importance: 4
novelty: 1
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.45

GitNexus v1.6.10-rc.45 於 2026 年 7 月 17 日 16:55 UTC 發佈，是 RC 版本系列的最後一個候選版本。聚焦 MCP 確定性政策系列（失敗封閉只讀、倉庫白名單、遠端 Bearer 認證、確定性預算）、CodeBuddy 和 Qoder 編碼代理整合、完整 Codex 支持（hooks、插件市場、安裝流程）、embeddings 和 FTS 自癒機制、Windows 平台穩定性加固（FTS 診斷、Napi SIGABRT 修復、符號索引行號映射）。快取/CLI/嵌入管道系列提供 HTTP 可恢復性、批量插入重試安全、解析檔案邊界控制、文本承載回退、樹 sitter NUL 位元組恢復、呼叫引用流程解析。作為預發佈版本供早期測試。

### 重點
- MCP 確定性政策系列完整落地：失敗封閉只讀模式、倉庫白名單強制、遠端綁定 Bearer 認證、確定性回應預算
- 多層次自癒機制：embeddings 安裝恢復、FTS 擴展自癒、嵌入管道復原
- Windows 平台加固：FTS 缺依賴診斷、Napi SIGABRT 修復、符號索引 0-based/1-based 映射、呼叫引用流程解析

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.45)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.10-rc.45

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.45 \n Target base: 1.6.10 (rc #45 )\n Source commit (main): ed8ab1c \n Release commit (versioned tree): 3a64234 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 fix(cli): make Claude skills discoverable by @magyargergo in #2434 
 chore(deps): npm audit fix — resolve @babel/core and brace-expansion advisories by @bong-water-water-bong in #2444 
 docs: document shared-first contributor setup by @100yenadmin in #2448 
 fix(mcp): context resource reads stale lastCommit/stats after out-of-process analyze ( #2438 ) by @magyargergo with @Copilot in #2439 
 feat: land determinism and MCP policy series ( #2458 #2482 #2464 #2465 #2478 #2480 #2462 #2460 ) by @magyargergo in #2511 
 feat(mcp): normalize impact and context parameter aliases by @100yenadmin in #2462 
 feat(mcp): add fail-closed read-only mode by @100yenadmin in #2464 
 feat(mcp): enforce repository allowlist and default by @100yenadmin in #2465 
 fix(communities): canonicalize projection order by @100yenadmin in #2478 
 fix(scope): stabilize graph lookup collisions by @100yenadmin in #2480 
 fix(scan): canonicalize traversal without order-sensitive bindings by @100yenadmin in #2482 
 feat(eval): require bearer auth for remote binding by @100yenadmin in #2458 
 feat(mcp): add deterministic response budgets by @100yenadmin in #2460 
 fix: land cache, CLI, and embeddings series ( #2476 #2470 #2455 #2468 ) by @magyargergo in #2512 
 fix(embeddings): make HTTP generation resumable by @100yenadmin in #2468 
 fix(cli): fail cypher errors loudly by @100yenadmin in #2470 
 fix(cache): bound parsedfile generations by @100yenadmin in #2476 
 fix(embeddings): fall back to text-bearing file nodes by @100yenadmin in #2455 
 test(embeddings): cover File-row deletion by @100yenadmin in #2513 
 ci: sync plugin manifests on version bumps and widen the Windows shard watchdog by @magyargergo in #2515 
 feat(taint): expand TS/JS sink model by @azizur100389 in #2490 
 feat(wiki): allow explicit HTTP LLM hosts by @azizur100389 in #2491 
 fix(mcp): avoid top-level api_impact schema combinators by @koriyoshi2041 in #2489 
 fix(embeddings): make batch inserts retry-safe by @koriyoshi2041 in #2453 
 test(cli): lock native load guard for analyze by @koriyoshi2041 in #2442 
 fix(scope-resolution): resolve callable reference flows ( #2437 ) by @magyargergo in #2522 
 
 New Contributors 
 
 @vlisitskii made their first contribution in #2424 
 @100yenadmin made their first contribution in #2451 
 @bong-water-water-bong made their first contribution in #2444 
 
 Full Changelog : v1.6.9...v1.6.10-rc.45

</details>