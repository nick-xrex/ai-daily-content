---
id: inbox_d69cbc1f
date: 2026-06-23
source_ref: "[[00-inbox/2026-06-23/2200-ruflo-releases-v3-14-1-4-user-reported-bug-fixes-2412-2-3607]]"
title: "v3.14.1 — 4 user-reported bug fixes (#2412, #2422, #2426, #2450)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.14.1
source: ruflo-releases
published_at: 2026-06-23T16:16:50+00:00
fetched_at: 2026-06-23T22:06:50.904340+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.14.1 補丁版本修復 4 項用戶報告的關鍵 bug。#2412 修復 pnpm lockfile 漂移導致 CI 5+ 天紅線；#2450 解決 statusline hooks 每次調用冷加載 ONNX 模型（~1s）導致 Claude Code 超時，通過正則擴展捕捉多種 hook 形式；#2426 修正 macOS MCP tools/list 響應（65,747 字節）超過 64KB 管道限制被截斷問題，設置 stdio 阻塞模式後支持完整傳遞 207,678 字節（3.17 倍限制）；#2422 更正文檔中記載的非實現功能。包含詳細驗證測試確保完整字節傳遞與正則覆蓋。"
key_points:
  - "pnpm lockfile 漂移導致 v3-ci.yml 5+ 天故障，重新生成 pnpm-lock.yaml 恢復；statusline ONNX 冷加載 (~1s) 通過正則擴展解決"
  - "macOS MCP 管道緩衝截斷修復：設置 stdio 阻塞模式（同 MCP SDK 官方 StdioServerTransport），tools/list 從 64KB 限制擴展至 207,678 字節完整傳遞"
  - "文檔修正：移除 5 種已實現模式（byzantine/raft/gossip/crdt/quorum）之外的非實現功能記載"
tags: [ruflo, mcp, ci-cd, bug-fix, macos]
topics: [agents.mcp]
importance: 4
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: true
deep_dive_approved: false
---

## v3.14.1 — 4 user-reported bug fixes (#2412, #2422, #2426, #2450)

ruflo v3.14.1 補丁版本修復 4 項用戶報告的關鍵 bug。#2412 修復 pnpm lockfile 漂移導致 CI 5+ 天紅線；#2450 解決 statusline hooks 每次調用冷加載 ONNX 模型（~1s）導致 Claude Code 超時，通過正則擴展捕捉多種 hook 形式；#2426 修正 macOS MCP tools/list 響應（65,747 字節）超過 64KB 管道限制被截斷問題，設置 stdio 阻塞模式後支持完整傳遞 207,678 字節（3.17 倍限制）；#2422 更正文檔中記載的非實現功能。包含詳細驗證測試確保完整字節傳遞與正則覆蓋。

### 重點
- pnpm lockfile 漂移導致 v3-ci.yml 5+ 天故障，重新生成 pnpm-lock.yaml 恢復；statusline ONNX 冷加載 (~1s) 通過正則擴展解決
- macOS MCP 管道緩衝截斷修復：設置 stdio 阻塞模式（同 MCP SDK 官方 StdioServerTransport），tools/list 從 64KB 限制擴展至 207,678 字節完整傳遞
- 文檔修正：移除 5 種已實現模式（byzantine/raft/gossip/crdt/quorum）之外的非實現功能記載

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.14.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release fixing four user-reported bugs across CI, MCP transport, init migration, and docs. 
 Fixes 
 
 #2412 — v3-ci.yml red on main for 5+ days (10+ verification recurrences). Lockfile drifted after version bumps in cli/package.json ; CI's pnpm install --frozen-lockfile failed on every job. Regenerated v3/pnpm-lock.yaml . 
 #2450 — hooks statusline cold-loaded the ONNX model on every invocation (~1s), Claude Code timed out the statusLine command and hid the status bar. #2448 's migration only caught the npx @latest form; broadened the regex to also catch the bare claude-flow hooks statusline form so existing settings.json files get rewritten on next ruflo init / doctor. 
 #2426 — On macOS, the MCP tools/list response (65,747 bytes for 314 tools) exceeded the 64KB pipe buffer and was truncated mid-frame, leaving Claude Code unable to register any MCP tools. Set stdout/stderr to blocking mode in stdio MCP server — same approach as the official MCP SDK's StdioServerTransport. 
 #2422 — docs/USERGUIDE.md documented Weighted (Queen 3×) / Majority consensus modes and Strategic/Tactical/Adaptive queen types that aren't wired in the shipped engine. Rewrote 4 USERGUIDE locations to the actually-shipped 5 modes: byzantine / raft / gossip / crdt / quorum. 
 
 Verification 
 
 pnpm install --frozen-lockfile exits 0 locally (CI's exact gate) 
 @claude-flow/cli builds clean with no new TS errors 
 Direct stdio probe: baseline truncates 70KB payload to exactly 65,536 bytes (matches #2426 reporter's number); with fix, full 83,146 bytes delivered intact across 3 runs 
 End-to-end smoke against published ruflo@3.14.1 : spawned ruflo mcp start in stdio mode, sent tools/list , received 207,678 bytes (305 tools) intact — 3.17× the pipe buffer limit 
 Statusline regex unit test: 7/7 (5 broken forms caught, 2 correct forms skipped) 
 grep "Weighted\|Queen 3" docs/USERGUIDE.md returns 0 matches 
 
 Install 
 npx ruflo@3.14.1
 # or 
npx @claude-flow/cli@3.14.1 
 All three packages — @claude-flow/cli , claude-flow , ruflo — at 3.14.1 with consistent latest === alpha === v3alpha dist-tags. 
 PR 
 #2454 — full diff, per-commit review available there.

</details>