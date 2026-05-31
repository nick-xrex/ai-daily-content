---
id: inbox_14be2339
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/0039-simon-willison-running-python-asgi-apps-in-the-browser-fb9a]]"
title: "Running Python ASGI apps in the browser via Pyodide + a service worker"
url: https://simonwillison.net/2026/May/30/pyodide-asgi-browser/#atom-everything
source: simon-willison
published_at: 2026-05-30T21:02:16+00:00
fetched_at: 2026-05-31T00:47:58.094613+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 用 Claude Opus 4.8 與 Claude Code（網頁版）解決「在瀏覽器運行 Python ASGI app」的架構設計難題。從原 Web Worker 方案（JavaScript 不執行、插件破損）改用 Service Worker，使 Datasette Lite 能執行 <script> 標籤，相容 Datasette 插件。已驗證 ASGI FastCGI demo 和 Datasette 1.0a31 在 Pyodide 環境正常運行。計畫升級 Datasette Lite 本身。展示 Claude Code 在技術架構決策中的實用性。"
key_points:
  - "方案遷移：Web Worker（JavaScript 被攔截，插件失效）→ Service Worker（JavaScript 可執行），根本解決相容性"
  - "工具應用：Claude Opus 4.8 + Claude Code（網頁版）快速迭代架構設計，減少手工推理開銷"
  - "驗證場景：ASGI FastCGI demo 和 Datasette 1.0a31 皆可在 Pyodide 運行，為 PWA 應用開發樹立新方向"
tags: [pyodide, service-worker, datasette, wasm, asgi]
topics: [foundation_models.claude]
importance: 2
novelty: 3
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Running Python ASGI apps in the browser via Pyodide + a service worker

Simon Willison 用 Claude Opus 4.8 與 Claude Code（網頁版）解決「在瀏覽器運行 Python ASGI app」的架構設計難題。從原 Web Worker 方案（JavaScript 不執行、插件破損）改用 Service Worker，使 Datasette Lite 能執行 <script> 標籤，相容 Datasette 插件。已驗證 ASGI FastCGI demo 和 Datasette 1.0a31 在 Pyodide 環境正常運行。計畫升級 Datasette Lite 本身。展示 Claude Code 在技術架構決策中的實用性。

### 重點
- 方案遷移：Web Worker（JavaScript 被攔截，插件失效）→ Service Worker（JavaScript 可執行），根本解決相容性
- 工具應用：Claude Opus 4.8 + Claude Code（網頁版）快速迭代架構設計，減少手工推理開銷
- 驗證場景：ASGI FastCGI demo 和 Datasette 1.0a31 皆可在 Pyodide 運行，為 PWA 應用開發樹立新方向

**原文：** [simon-willison](https://simonwillison.net/2026/May/30/pyodide-asgi-browser/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Research: Running Python ASGI apps in the browser via Pyodide + a service worker 
 Datasette Lite is my version of Datasette that runs entirely in the browser using Pyodide in WebAssembly. 
 When I first built it four years ago I used Web Workers and code that intercepts navigation operations and fetches the generated HTML by running the Python app. 
 This worked, but had the disadvantage that any JavaScript in &lt;script&gt; tags would not be executed - breaking some Datasette functionality and a whole lot of Datasette plugins. 
 This morning I set Claude Opus 4.8 the task (in Claude Code for web) of figuring out how to run Python ASGI apps in Pyodide using Service Workers instead, and it seems to work! Here's a basic ASGI FastCGI demo and here's a demo that runs Datasette 1.0a31 . 
 I'm still getting my head around exactly how it works, but once I've done that I plan to upgrade Datasette Lite itself. 
 
 
 Tags: javascript , python , datasette , asgi , service-workers , pyodide , datasette-lite , claude-code

</details>