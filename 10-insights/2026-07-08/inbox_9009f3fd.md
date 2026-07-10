---
id: inbox_9009f3fd
date: 2026-07-08
source_ref: "[[00-inbox/.../inbox_9009f3fd]]"
title: "Release Candidate v1.6.10-rc.9"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.9
source: gitnexus-releases
published_at: 2026-07-08T17:49:43+00:00
fetched_at: 2026-07-10T00:43:20.660811+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.9 累積多項編碼代理集成與穩定性改進。新增 CodeBuddy 和 Qoder 編碼代理支持，以及完整 Codex hooks 與 plugin marketplace 機制（#2369，前身為 #1131）。針對常見部署場景修復關鍵錯誤：proxy-blocked 環境下 onnxruntime-node 自修復（#2372）、Windows FTS 和 shadow 依賴診斷（#2383、#2387）、MCP symbol 內容與行號儲存的 0-based/1-based 轉換（#2380）、自定義 embedding endpoint 錯誤報告（#2386）。引入 MCP query hint 機制（#2397），當 GitNexus MCP server 持有寫鎖時主動提示 agent 使用 mcp__gitnexus__query 工具，替代無聲跳過。Windows CI 矩陣 sharding 改進解決跨平台超時問題（#2394）。"
key_points:
  - "新增 CodeBuddy/Qoder 代理集成 + 完整 Codex hooks/plugin marketplace（#2369），擴展編碼代理協作能力"
  - "MCP symbol content 與行號儲存修正：0-based 本地 ↔ 1-based MCP display（#2377/#2379/#2380），保證編輯器與 MCP 工具行號一致"
  - "MCP query hint 機制（#2396/#2397）：當 MCP server 持有 DB 寫鎖時發出條件性 hint 而非無聲跳過，增強 server-owned 部署模式下的 agent 可見性"
tags: [codex-integration, mcp-server, agent-coordination, error-recovery, windows-compat]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.9

GitNexus v1.6.10-rc.9 累積多項編碼代理集成與穩定性改進。新增 CodeBuddy 和 Qoder 編碼代理支持，以及完整 Codex hooks 與 plugin marketplace 機制（#2369，前身為 #1131）。針對常見部署場景修復關鍵錯誤：proxy-blocked 環境下 onnxruntime-node 自修復（#2372）、Windows FTS 和 shadow 依賴診斷（#2383、#2387）、MCP symbol 內容與行號儲存的 0-based/1-based 轉換（#2380）、自定義 embedding endpoint 錯誤報告（#2386）。引入 MCP query hint 機制（#2397），當 GitNexus MCP server 持有寫鎖時主動提示 agent 使用 mcp__gitnexus__query 工具，替代無聲跳過。Windows CI 矩陣 sharding 改進解決跨平台超時問題（#2394）。

### 重點
- 新增 CodeBuddy/Qoder 代理集成 + 完整 Codex hooks/plugin marketplace（#2369），擴展編碼代理協作能力
- MCP symbol content 與行號儲存修正：0-based 本地 ↔ 1-based MCP display（#2377/#2379/#2380），保證編輯器與 MCP 工具行號一致
- MCP query hint 機制（#2396/#2397）：當 MCP server 持有 DB 寫鎖時發出條件性 hint 而非無聲跳過，增強 server-owned 部署模式下的 agent 可見性

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.9)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.10-rc.9

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.9 \n Target base: 1.6.10 (rc #9 )\n Source commit (main): 1408bfb \n Release commit (versioned tree): 572cb93 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 
 Full Changelog : v1.6.9...v1.6.10-rc.9

</details>