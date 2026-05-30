---
id: inbox_afe1e220
date: 2026-05-29
source_ref: "[[00-inbox/2026-05-29/0216-claude-mem-releases-v13-4-0-e30f]]"
title: "v13.4.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.4.0
source: claude-mem-releases
published_at: 2026-05-29T18:35:01+00:00
fetched_at: 2026-05-30T02:25:00.428595+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.4.0 大規模缺陷清除：測試 46→0 失敗，typecheck 24→0 錯誤。新增 OpenAI 兼容基礎 URL 配置環境變數 CLAUDE_MEM_OPENROUTER_BASE_URL，可指向 DeepSeek、LM Studio 或自訂端點。修復涉及 Spawn contract 的 ${CLAUDE_PLUGIN_ROOT} 解析與 Windows spawn (codex.cmd、chroma-mcp cmd.exe 引號)、Worker lifecycle PID 重用啟動令牌守衛、Output fidelity 的提交哈希驗證與 null-cwd 不再剝離十六進制字符、SQLite schema 修復 via .recover 與錯誤路徑的 DB 句柄關閉、SessionMessageBuffer clear() 重置 dedup 集合允許重複 toolUseId。新 CI 工作流整合 typecheck/build/test/bundle-size 和 Docker pg+valkey e2e。"
key_points:
  - "OpenAI 兼容端點配置 CLAUDE_MEM_OPENROUTER_BASE_URL → 支援 DeepSeek、LM Studio 等自訂 API 端點"
  - "SQLite .recover 模式自修復 + 錯誤路徑 DB 句柄關閉 → 防止寫入鎖洩漏"
  - "跨平台 spawn 修復（${CLAUDE_PLUGIN_ROOT} 解析、Windows cmd.exe 引號、PID 重用防護）→ Worker lifecycle 穩定性"
tags: [cross-platform, windows-compatibility, sqlite, test-infrastructure, provider-extensibility]
topics: []
importance: 4
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.4.0

claude-mem v13.4.0 大規模缺陷清除：測試 46→0 失敗，typecheck 24→0 錯誤。新增 OpenAI 兼容基礎 URL 配置環境變數 CLAUDE_MEM_OPENROUTER_BASE_URL，可指向 DeepSeek、LM Studio 或自訂端點。修復涉及 Spawn contract 的 ${CLAUDE_PLUGIN_ROOT} 解析與 Windows spawn (codex.cmd、chroma-mcp cmd.exe 引號)、Worker lifecycle PID 重用啟動令牌守衛、Output fidelity 的提交哈希驗證與 null-cwd 不再剝離十六進制字符、SQLite schema 修復 via .recover 與錯誤路徑的 DB 句柄關閉、SessionMessageBuffer clear() 重置 dedup 集合允許重複 toolUseId。新 CI 工作流整合 typecheck/build/test/bundle-size 和 Docker pg+valkey e2e。

### 重點
- OpenAI 兼容端點配置 CLAUDE_MEM_OPENROUTER_BASE_URL → 支援 DeepSeek、LM Studio 等自訂 API 端點
- SQLite .recover 模式自修復 + 錯誤路徑 DB 句柄關閉 → 防止寫入鎖洩漏
- 跨平台 spawn 修復（${CLAUDE_PLUGIN_ROOT} 解析、Windows cmd.exe 引號、PID 重用防護）→ Worker lifecycle 穩定性

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.4.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

v13.4.0 — Defect backlog clearance + provider extensibility 
 Clears a large defect backlog (plans 01–11 plus standalone fixes) and adds provider configurability. Test suite moved 46 → 0 failing and typecheck 24 → 0 errors over the branch. 
 Features 
 
 Configurable OpenAI-compatible base URL for the OpenRouter provider ( CLAUDE_MEM_OPENROUTER_BASE_URL ) — point claude-mem at DeepSeek, LM Studio, or any custom OpenAI-compatible endpoint. 
 
 Fixes (highlights) 
 
 Spawn contract (plan-02): canonical ${CLAUDE_PLUGIN_ROOT} resolution + Windows spawn fixes (codex.cmd, chroma-mcp cmd.exe quoting). 
 Worker lifecycle (plan-03): Windows PID-reuse start-token guard. 
 Output fidelity (plan-11): commit-hash verification before persist; null- cwd no longer strips every hex string from summaries. 
 SQLite self-healing: schema repair via sqlite3 .recover ; close DB handle on repair error paths (no leaked write lock). 
 SessionMessageBuffer: clear() now also resets the dedup set, so a previously-seen toolUseId can re-enter. 
 Standalone: project name, dot-path encoding, path-match, CLAUDE.md denylist. 
 
 CI / tests 
 
 New CI workflow (typecheck · build · test · bundle-size + docker pg+valkey e2e) made green; removed npm-lockfile dependency to match the repo's no-committed-lockfile convention. 
 Fixed mock.module logger leakage across test files and guarded sqlite3 .recover capability so CI runs cleanly. 
 
 Full diff: #2701

</details>