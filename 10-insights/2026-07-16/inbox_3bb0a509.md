---
id: inbox_3bb0a509
date: 2026-07-16
source_ref: "[[00-inbox/2026-07-16/0146-simon-willison-mermaid-to-unicode-box-art-grok-mermaid-9969]]"
title: "Mermaid to Unicode box art (grok-mermaid)"
url: https://simonwillison.net/2026/Jul/16/grok-mermaid/#atom-everything
source: simon-willison
published_at: 2026-07-16T00:33:18+00:00
fetched_at: 2026-07-16T01:51:59.316661+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 介紹了 grok-mermaid 工具，一個自包含的 Rust 終端渲染器，可將 Mermaid 圖表轉換為 Unicode 方塊藝術。此工具源自 xAI 最近開源的 Grok Build 代碼庫（xai-grok-markdown/src/mermaid.rs）。Willison 使用 Claude Code for web (Fable 5) 將此 Rust 實現編譯為 WebAssembly，使其可在瀏覽器中直接執行，無需服務端支持。"
key_points:
  - "grok-mermaid 是自包含的 Rust 終端渲染器，支持 Mermaid 圖表子集，使用 Unicode 方塊繪製"
  - "通過 WebAssembly 編譯後可在瀏覽器無縫執行，展示 Claude Code 在編譯工具中的應用"
  - "源自 xAI 開源代碼庫，展示編碼代理中的圖表渲染實現模式"
tags: [tool, mermaid, rust, webassembly, unicode-rendering]
topics: []
importance: 2
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Mermaid to Unicode box art (grok-mermaid)

Simon Willison 介紹了 grok-mermaid 工具，一個自包含的 Rust 終端渲染器，可將 Mermaid 圖表轉換為 Unicode 方塊藝術。此工具源自 xAI 最近開源的 Grok Build 代碼庫（xai-grok-markdown/src/mermaid.rs）。Willison 使用 Claude Code for web (Fable 5) 將此 Rust 實現編譯為 WebAssembly，使其可在瀏覽器中直接執行，無需服務端支持。

### 重點
- grok-mermaid 是自包含的 Rust 終端渲染器，支持 Mermaid 圖表子集，使用 Unicode 方塊繪製
- 通過 WebAssembly 編譯後可在瀏覽器無縫執行，展示 Claude Code 在編譯工具中的應用
- 源自 xAI 開源代碼庫，展示編碼代理中的圖表渲染實現模式

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/16/grok-mermaid/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tool: Mermaid to Unicode box art (grok-mermaid) 
 While exploring the codebase for the newly open-sourced Grok CLI coding agent I came across xai-grok-markdown/src/mermaid.rs , a "self-contained terminal renderer for Mermaid diagrams" written in Rust. 
 I figured it would be fun to try that out in a browser via WebAssembly. Here's the prompt I ran in Claude Code for web (Fable 5), and this is what the resulting tool looks like: 
 
 
 
 Tags: tools , rust , webassembly , mermaid , grok , xai

</details>