---
id: inbox_8c9a9273
date: 2026-07-16
source_ref: "[[00-inbox/.../inbox_8c9a9273]]"
title: "Release Candidate v1.6.10-rc.31"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.31
source: gitnexus-releases
published_at: 2026-07-16T12:24:00+00:00
fetched_at: 2026-07-17T00:47:19.352422+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.31 是針對 v1.6.10 版本的自動化發布候選構建（rc #31），包含近 30 項新功能與修復。主要新增 CodeBuddy 與 Qoder 編碼代理集成、完整 Codex 支持（hooks、plugin marketplace）、Determinism 與 MCP 政策系列實現。修復涵蓋 Windows FTS 與 onnxruntime 安裝難題、Napi::Error SIGABRT 死機、MCP 符號精確性（0-based vs 1-based 行編號協議對齊）、tree-sitter 從嵌入式 NUL 字節恢復、HTTP 嵌入端點錯誤報告。新增三位貢獻者，基礎版本升級自 v1.6.9。"
key_points:
  - "CodeBuddy + Qoder 代理集成與完整 Codex 支持（hooks、plugin marketplace、setup）"
  - "Determinism + MCP policy series 確保查詢確定性與資源預算約束（涵蓋 #2458-#2482 共 8 個相關 PR）"
  - "Windows 跨平台穩定性：FTS 依賴診斷、Napi::Error SIGABRT 修復、tree-sitter NUL 字節恢復、buffer manager 非標準頁大小診斷"
tags: [gitnexus-release, mcp-improvements, codex-support, agent-integration, windows-stability]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.31

GitNexus v1.6.10-rc.31 是針對 v1.6.10 版本的自動化發布候選構建（rc #31），包含近 30 項新功能與修復。主要新增 CodeBuddy 與 Qoder 編碼代理集成、完整 Codex 支持（hooks、plugin marketplace）、Determinism 與 MCP 政策系列實現。修復涵蓋 Windows FTS 與 onnxruntime 安裝難題、Napi::Error SIGABRT 死機、MCP 符號精確性（0-based vs 1-based 行編號協議對齊）、tree-sitter 從嵌入式 NUL 字節恢復、HTTP 嵌入端點錯誤報告。新增三位貢獻者，基礎版本升級自 v1.6.9。

### 重點
- CodeBuddy + Qoder 代理集成與完整 Codex 支持（hooks、plugin marketplace、setup）
- Determinism + MCP policy series 確保查詢確定性與資源預算約束（涵蓋 #2458-#2482 共 8 個相關 PR）
- Windows 跨平台穩定性：FTS 依賴診斷、Napi::Error SIGABRT 修復、tree-sitter NUL 字節恢復、buffer manager 非標準頁大小診斷

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.31)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.10-rc.31

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.31 \n Target base: 1.6.10 (rc #31 )\n Source commit (main): 573a777 \n Release commit (versioned tree): 2f299bb \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @vlisitskii made their first contribution in #2424 
 @100yenadmin made their first contribution in #2451 
 @bong-water-water-bong made their first contribution in #2444 
 
 Full Changelog : v1.6.9...v1.6.10-rc.31

</details>