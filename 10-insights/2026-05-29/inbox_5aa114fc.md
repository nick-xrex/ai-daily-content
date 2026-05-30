---
id: inbox_5aa114fc
date: 2026-05-29
source_ref: "[[00-inbox/2026-05-29/0216-ruflo-releases-v3-10-12-agentdb-upstream-fix-closes-223-9612]]"
title: "v3.10.12 — agentdb upstream fix (closes #2235 A)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.12
source: ruflo-releases
published_at: 2026-05-29T23:01:38+00:00
fetched_at: 2026-05-30T02:24:09.159082+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.12 更新捆綁的 agentdb 至 3.0.0-alpha.15，啟用了 MCP 記憶橋接中可選的 better-sqlite3。修復了讓 loadSchemas() 在瀏覽器與全局安裝 CLI 中工作的上游 bug（ruvnet/agentdb#1、#2），schema 改為內聯為捆綁字符串常數。此修復實現了 issue #2235 part (A) 的完整閉合。"
key_points:
  - "agentdb 升至 3.0.0-alpha.15，啟用 better-sqlite3 for MCP memory bridge"
  - "Schema 內聯為捆綁字符串常數，解決瀏覽器與全局 CLI 中 loadSchemas() 失效問題"
  - "關閉 ruflo#2235 (A) 與上游 agentdb#1、#2"
tags: [mcp-integration, memory-bridge, schema-fix]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.12 — agentdb upstream fix (closes #2235 A)

Ruflo v3.10.12 更新捆綁的 agentdb 至 3.0.0-alpha.15，啟用了 MCP 記憶橋接中可選的 better-sqlite3。修復了讓 loadSchemas() 在瀏覽器與全局安裝 CLI 中工作的上游 bug（ruvnet/agentdb#1、#2），schema 改為內聯為捆綁字符串常數。此修復實現了 issue #2235 part (A) 的完整閉合。

### 重點
- agentdb 升至 3.0.0-alpha.15，啟用 better-sqlite3 for MCP memory bridge
- Schema 內聯為捆綁字符串常數，解決瀏覽器與全局 CLI 中 loadSchemas() 失效問題
- 關閉 ruflo#2235 (A) 與上游 agentdb#1、#2

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.12)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Bumps the bundled agentdb to 3.0.0-alpha.15 so the optionally-installed 
 better-sqlite3 is finally engaged by the MCP memory bridge — the part (A) 
half of #2235 that was upstream-only. 
 The matching agentdb fix also closes ruvnet/agentdb#1 and #2 (schemas inlined as bundled string constants so loadSchemas() works in the browser and in globally-installed CLIs). 
 Install: npx ruflo@3.10.12 
 Closes: ruflo#2235 (A).

</details>