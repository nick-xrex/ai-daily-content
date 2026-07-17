---
id: inbox_f57e5bca
date: 2026-07-16
source_ref: "[[00-inbox/.../inbox_f57e5bca]]"
title: "Release Candidate v1.6.10-rc.35"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.35
source: gitnexus-releases
published_at: 2026-07-16T15:09:34+00:00
fetched_at: 2026-07-17T00:45:22.633179+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.35 新增嵌入向量批次插入重試安全機制與 CLI 原生載入守衛測試，進一步強化系統韌性。版本積累了 CodeBuddy/Qoder 代理整合、Codex 支援、Wiki HTTP 配置、MCP 協議修復等功能。重點改進包括嵌入向量處理管道的可靠性（批次插入重試安全、#2453）、測試覆蓋增強（native load guard、#2442），以及先前版本的全面穩定性修復（Windows 相容性、FTS 診斷、C++ 型別查詢）。"
key_points:
  - "嵌入向量管道韌性提升：批次插入重試安全機制（#2453），確保插入操作可恢復"
  - "測試覆蓋擴大：CLI 原生載入守衛測試（#2442），驗證載入安全性"
  - "累積穩定性：MCP 協議相容性、Windows 跨平台修復、C++ 型別查詢索引化、分析器 NUL 位元組恢復"
tags: [gitnexus, codex-integration, embeddings-reliability, test-coverage, mcp-protocol]
topics: [foundation_models.gpt, agents.mcp]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.35

GitNexus v1.6.10-rc.35 新增嵌入向量批次插入重試安全機制與 CLI 原生載入守衛測試，進一步強化系統韌性。版本積累了 CodeBuddy/Qoder 代理整合、Codex 支援、Wiki HTTP 配置、MCP 協議修復等功能。重點改進包括嵌入向量處理管道的可靠性（批次插入重試安全、#2453）、測試覆蓋增強（native load guard、#2442），以及先前版本的全面穩定性修復（Windows 相容性、FTS 診斷、C++ 型別查詢）。

### 重點
- 嵌入向量管道韌性提升：批次插入重試安全機制（#2453），確保插入操作可恢復
- 測試覆蓋擴大：CLI 原生載入守衛測試（#2442），驗證載入安全性
- 累積穩定性：MCP 協議相容性、Windows 跨平台修復、C++ 型別查詢索引化、分析器 NUL 位元組恢復

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.35)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.10-rc.35

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.35 \n Target base: 1.6.10 (rc #35 )\n Source commit (main): 8292b2b \n Release commit (versioned tree): c86e886 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @vlisitskii made their first contribution in #2424 
 @100yenadmin made their first contribution in #2451 
 @bong-water-water-bong made their first contribution in #2444 
 
 Full Changelog : v1.6.9...v1.6.10-rc.35

</details>