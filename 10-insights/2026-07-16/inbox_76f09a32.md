---
id: inbox_76f09a32
date: 2026-07-16
source_ref: "[[00-inbox/.../inbox_76f09a32]]"
title: "Release Candidate v1.6.10-rc.28"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.28
source: gitnexus-releases
published_at: 2026-07-16T10:25:36+00:00
fetched_at: 2026-07-17T00:47:19.357658+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.28 是快速迭代序列的更早階段版本。與 rc.29 相比，changelog 進一步精簡，缺少若干 MCP 政策系列提交（特別是 deterministic response budgets #2460、plugin manifest sync #2515）。此版本為上游基礎，標誌著 rc 系列的演進起點，展現逐次功能疊加、增量修復的發布流程。"
key_points:
  - "Codex 與代理集成的基礎功能在 rc.28 版本已達成"
  - "Deterministic response budgets (#2460) 與 plugin manifest sync 為 rc.28 後版本新加入"
  - "發布候選快速疊代過程展現功能漸進整合、Windows 穩定性優化持續深化"
tags: [gitnexus-rc-early, ci-pipeline, version-tracking]
topics: [agents.mcp]
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.28

GitNexus v1.6.10-rc.28 是快速迭代序列的更早階段版本。與 rc.29 相比，changelog 進一步精簡，缺少若干 MCP 政策系列提交（特別是 deterministic response budgets #2460、plugin manifest sync #2515）。此版本為上游基礎，標誌著 rc 系列的演進起點，展現逐次功能疊加、增量修復的發布流程。

### 重點
- Codex 與代理集成的基礎功能在 rc.28 版本已達成
- Deterministic response budgets (#2460) 與 plugin manifest sync 為 rc.28 後版本新加入
- 發布候選快速疊代過程展現功能漸進整合、Windows 穩定性優化持續深化

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.28)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.10-rc.28

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.28 \n Target base: 1.6.10 (rc #28 )\n Source commit (main): 318754e \n Release commit (versioned tree): a3cad5b \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @vlisitskii made their first contribution in #2424 
 @100yenadmin made their first contribution in #2451 
 @bong-water-water-bong made their first contribution in #2444 
 
 Full Changelog : v1.6.9...v1.6.10-rc.28

</details>