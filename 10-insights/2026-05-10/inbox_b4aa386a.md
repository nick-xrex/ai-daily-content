---
id: inbox_b4aa386a
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_b4aa386a]]"
title: "v13.0.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.0.1
source: claude-mem-releases
published_at: 2026-05-10T07:26:31+00:00
fetched_at: 2026-06-04T00:59:24.193866+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.0.1 發布，修復多項關鍵穩定性與安全隱患。MCP 伺服器層面修正 .mcp.json 參數擴展驗證問題；環境隔離增強實現三分支 OAuth 跳過謂詞以阻止 ANTHROPIC_BASE_URL 洩露；Worker 生命週期改進包括 Claude SDK HTTP 400 錯誤分類與 Chroma MCP 單例強制執行；build 層支援 ESM import.meta.url polyfill；新增三個 Chroma MCP 回歸測試確保單例模式，並修復 macOS arm64 protobuf < 7 版本衝突。"
key_points:
  - "修復 MCP validator 參數擴展問題（${_R%/} 修剪），解決 Claude Code 驗證失敗：#2371"
  - "環境隔離強化：三分支 OAuth 跳過謂詞防止 ANTHROPIC_BASE_URL 洩露跨 OAuth 流；#2357"
  - "Chroma MCP 單例強制執行 + macOS arm64 protobuf 版本修復 (onnxruntime ≥1.20, protobuf <7)，解決跨平台相容性崩潰；#2313"
tags: [claude-mem, mcp-server, bug-fix, security-hardening]
topics: [agents.mcp, foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.0.1

claude-mem v13.0.1 發布，修復多項關鍵穩定性與安全隱患。MCP 伺服器層面修正 .mcp.json 參數擴展驗證問題；環境隔離增強實現三分支 OAuth 跳過謂詞以阻止 ANTHROPIC_BASE_URL 洩露；Worker 生命週期改進包括 Claude SDK HTTP 400 錯誤分類與 Chroma MCP 單例強制執行；build 層支援 ESM import.meta.url polyfill；新增三個 Chroma MCP 回歸測試確保單例模式，並修復 macOS arm64 protobuf < 7 版本衝突。

### 重點
- 修復 MCP validator 參數擴展問題（${_R%/} 修剪），解決 Claude Code 驗證失敗：#2371
- 環境隔離強化：三分支 OAuth 跳過謂詞防止 ANTHROPIC_BASE_URL 洩露跨 OAuth 流；#2357
- Chroma MCP 單例強制執行 + macOS arm64 protobuf 版本修復 (onnxruntime ≥1.20, protobuf <7)，解決跨平台相容性崩潰；#2313

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.0.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.0.1

Bug fixes 
 MCP server 
 
 #2371 — drop ${_R%/} parameter-expansion trim in .mcp.json that tripped Claude Code's MCP validator 
 
 Environment isolation 
 
 #2357 — block ANTHROPIC_BASE_URL leak; use a three-branch OAuth-skip predicate 
 Add CLAUDE_MEM_ENV_FILE lazy resolver so tests (and multi-profile users) can redirect the env-file path without module-load-order constraints 
 
 Worker lifecycle 
 
 Classify Claude SDK HTTP 400 as unrecoverable so the worker stops retrying a doomed request 
 Stop hook crash hardened: onclose handler now performs background tree-kill on unexpected subprocess exit 
 
 Chroma 
 
 #2313 — enforce a single chroma-mcp subprocess per worker (singleton via disposeCurrentSubprocess() on every code path; tree-kill of orphans on dispose) 
 Pin onnxruntime&gt;=1.20 and protobuf&lt;7 to fix INVALID_PROTOBUF on macOS arm64 
 
 Build 
 
 Polyfill import.meta.url to pathToFileURL(__filename) in the CJS worker bundle so ESM-style code resolves correctly (CodeRabbit-driven follow-up) 
 
 Tests / review 
 
 tests/env-isolation.test.ts no longer mutates the real ~/.claude-mem/.env ; OAuth spy wrapped in try/finally to avoid leaks across runs 
 3 new chroma-mcp regression tests for #2313 (singleton enforcement) 
 
 Misc 
 
 Daily dependency bump per CLAUDE.md maintenance policy 
 
 Full diff: #2394

</details>