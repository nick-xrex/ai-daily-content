---
id: inbox_88df891a
date: 2026-06-23
source_ref: "[[00-inbox/2026-06-23/2200-simon-willison-opfs-pyodide-test-harness-1963]]"
title: "OPFS + Pyodide test harness"
url: https://simonwillison.net/2026/Jun/23/opfs-pyodide/#atom-everything
source: simon-willison
published_at: 2026-06-23T18:58:54+00:00
fetched_at: 2026-06-23T22:08:01.612767+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 使用 Claude Code 為 Datasette Lite 建立了一個測試工具，結合 OPFS（Origin Private File System）和 Pyodide，目的是驗證在瀏覽器中編輯用戶電腦上的持久化 SQLite 文件是否可行。該工具使用 WebAssembly 和 Python，支援跨瀏覽器測試。這展示了 Claude Code 在快速原型開發中的應用，特別是當主專案作為並行工作時。該工具可供開發者測試和改進。"
key_points:
  - "結合 OPFS + Pyodide + SQLite，實現瀏覽器端持久化文件編輯"
  - "由 Claude Code 自動建置完整 UI，展示編碼代理的快速原型能力"
  - "支援跨瀏覽器（Chrome、Firefox、Safari）測試，驗證兼容性"
tags: [opfs, pyodide, wasm, datasette-lite, browser-storage]
topics: []
importance: 3
novelty: 3
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## OPFS + Pyodide test harness

Simon Willison 使用 Claude Code 為 Datasette Lite 建立了一個測試工具，結合 OPFS（Origin Private File System）和 Pyodide，目的是驗證在瀏覽器中編輯用戶電腦上的持久化 SQLite 文件是否可行。該工具使用 WebAssembly 和 Python，支援跨瀏覽器測試。這展示了 Claude Code 在快速原型開發中的應用，特別是當主專案作為並行工作時。該工具可供開發者測試和改進。

### 重點
- 結合 OPFS + Pyodide + SQLite，實現瀏覽器端持久化文件編輯
- 由 Claude Code 自動建置完整 UI，展示編碼代理的快速原型能力
- 支援跨瀏覽器（Chrome、Firefox、Safari）測試，驗證兼容性

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/23/opfs-pyodide/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tool: OPFS + Pyodide test harness 
 I've been pondering if Datasette Lite - the Python Datasette application run entirely in the browser using Pyodide and WebAssembly - might be able to edit persistent SQLite files stored on the user's computer. 
 That's what OFPS (Origin Private File System) is for, so I had Claude Code for web build me this playground UI to try it out in different browsers. 
 
 
 Tags: browsers , pyodide , datasette-lite

</details>