---
id: inbox_0deb9cd4
date: 2026-06-29
source_ref: "[[00-inbox/.../inbox_0deb9cd4]]"
title: "v13.9.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.9.1
source: claude-mem-releases
published_at: 2026-06-29T23:47:48+00:00
fetched_at: 2026-07-02T01:14:54.789944+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.9.1 是補丁版本，主要合併平台來源恢復工作（#3088）並強化各項依賴。修復清單包括：Codex 啟動上下文優先透過 MCP 載入（HTTP fallback 到 worker），避免 shell 生成安裝程序；記憶恢復按平台來源範圍化，防止跨平台污染；Observer 在配額達上限時暫停；Chroma 預熱 uvx 並強化關閉流程；依賴健康檢查失敗時優雅降級。測試方面修復了會話初始化穩定性，且恢復 Chroma MCP mock 以防止跨測試套件洩漏。"
key_points:
  - "平台來源恢復機制：記憶按來源範圍化，防止跨平台數據污染"
  - "Codex MCP 優先層級：首選 MCP 載入，HTTP fallback 到 worker（避免 shell 生成）"
  - "依賴健康與優雅降級：預檢缺失 CLI 依賴並降級（chroma harden，telemetry UUIDv5 替換）"
tags: [claude-mem, platform-recovery, codex, mcp]
topics: [foundation_models.claude]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.9.1

claude-mem v13.9.1 是補丁版本，主要合併平台來源恢復工作（#3088）並強化各項依賴。修復清單包括：Codex 啟動上下文優先透過 MCP 載入（HTTP fallback 到 worker），避免 shell 生成安裝程序；記憶恢復按平台來源範圍化，防止跨平台污染；Observer 在配額達上限時暫停；Chroma 預熱 uvx 並強化關閉流程；依賴健康檢查失敗時優雅降級。測試方面修復了會話初始化穩定性，且恢復 Chroma MCP mock 以防止跨測試套件洩漏。

### 重點
- 平台來源恢復機制：記憶按來源範圍化，防止跨平台數據污染
- Codex MCP 優先層級：首選 MCP 載入，HTTP fallback 到 worker（避免 shell 生成）
- 依賴健康與優雅降級：預檢缺失 CLI 依賴並降級（chroma harden，telemetry UUIDv5 替換）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.9.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.9.1

What's Changed 
 Patch release shipping the platform-source recovery work merged in #3088 , plus dependency and Codex hardening. 
 Fixes 
 
 codex: load startup context through MCP, with HTTP fallback to the worker 
 codex: avoid shell spawning the Codex installer 
 recovery: scope memories by platform source 
 observer: drop invalid prose and pause on quota 
 chroma: prewarm uvx and harden shutdown 
 deps: surface dependency-health preflight and degrade gracefully when CLI deps are missing 
 telemetry: replace Bun UUIDv5 dependency 
 
 Tests 
 
 Stabilize session init after the server rename 
 Restore Chroma MCP mock to prevent cross-suite leakage 
 
 Full Changelog : v13.9.0...v13.9.1

</details>