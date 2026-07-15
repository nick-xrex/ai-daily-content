---
id: inbox_782aa59e
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-gitnexus-releases-release-candidate-v1-6-10-rc-20-bf38]]"
title: "Release Candidate v1.6.10-rc.20"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.20
source: gitnexus-releases
published_at: 2026-07-14T02:23:03+00:00
fetched_at: 2026-07-14T22:07:29.887775+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.20 發佈（第 20 號 RC，npm 安裝：npm install gitnexus@rc）。新增完整 Codex 支持（hooks、plugin marketplace、setup）及 CodeBuddy 和 Qoder 編碼代理集成。修復層面包括代理安裝穩定性（onnxruntime-node postinstall 自癒）、FTS extension load errors、MCP 符號精度（0-based 行號存儲 vs 1-based MCP 顯示）、Windows FTS 依賴診斷、嵌入端點錯誤報告、FastAPI 路由解析、大型增量寫回可靠性及 tree-sitter NUL 字節恢復。約 30 項變更，涵蓋核心、Web UI、CI/CD 與 MCP 集成多個層面。"
key_points:
  - "完整 Codex 支持（hooks、plugin marketplace）及 CodeBuddy/Qoder 代理集成"
  - "修復 MCP 符號精度問題（0-based 行號存儲）及代理安裝自癒機制"
  - "Windows 平台 FTS 診斷與 CI 矩陣分片優化，提升跨平台穩定性"
tags: [gitnexus, rc-release, codex-integration, mcp, coding-agents]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.20

GitNexus v1.6.10-rc.20 發佈（第 20 號 RC，npm 安裝：npm install gitnexus@rc）。新增完整 Codex 支持（hooks、plugin marketplace、setup）及 CodeBuddy 和 Qoder 編碼代理集成。修復層面包括代理安裝穩定性（onnxruntime-node postinstall 自癒）、FTS extension load errors、MCP 符號精度（0-based 行號存儲 vs 1-based MCP 顯示）、Windows FTS 依賴診斷、嵌入端點錯誤報告、FastAPI 路由解析、大型增量寫回可靠性及 tree-sitter NUL 字節恢復。約 30 項變更，涵蓋核心、Web UI、CI/CD 與 MCP 集成多個層面。

### 重點
- 完整 Codex 支持（hooks、plugin marketplace）及 CodeBuddy/Qoder 代理集成
- 修復 MCP 符號精度問題（0-based 行號存儲）及代理安裝自癒機制
- Windows 平台 FTS 診斷與 CI 矩陣分片優化，提升跨平台穩定性

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.20)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.20 \n Target base: 1.6.10 (rc #20 )\n Source commit (main): f6c63f6 \n Release commit (versioned tree): 7de2b3f \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 New Contributors 
 
 @vlisitskii made their first contribution in #2424 
 
 Full Changelog : v1.6.9...v1.6.10-rc.20

</details>