---
id: inbox_ada93a86
date: 2026-05-28
source_ref: "[[00-inbox/2026-05-28/0216-simon-willison-markdown-svg-renderer-08b2]]"
title: "markdown-svg-renderer"
url: https://simonwillison.net/2026/May/28/markdown-svg-renderer/#atom-everything
source: simon-willison
published_at: 2026-05-28T19:45:14+00:00
fetched_at: 2026-05-30T02:26:17.268999+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 發布 markdown-svg-renderer 工具。這是一個 Markdown 渲染器，對 fenced SVG code blocks 提供特殊處理：既能渲染 SVG 圖像，也能切換到代碼檢視模式。支援直接貼上 Markdown 內容或提供 URL（需啟用 CORS）。示例應用為渲染 LLM pelican 日誌（與 Claude Opus 4.8 實驗相關）。"
key_points:
  - "功能：Markdown 渲染 + SVG fenced code block 雙重檢視（圖像 + 代碼）"
  - "輸入方式：直接貼 Markdown 或提供 CORS 啟用的 URL"
  - "應用場景：LLM 實驗日誌可視化（如 Opus 4.8 pelican 圖像生成日誌）"
tags: [tool, markdown, svg, renderer, visualization]
topics: []
importance: 1
novelty: 2
insight_quality: 1
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## markdown-svg-renderer

Simon Willison 發布 markdown-svg-renderer 工具。這是一個 Markdown 渲染器，對 fenced SVG code blocks 提供特殊處理：既能渲染 SVG 圖像，也能切換到代碼檢視模式。支援直接貼上 Markdown 內容或提供 URL（需啟用 CORS）。示例應用為渲染 LLM pelican 日誌（與 Claude Opus 4.8 實驗相關）。

### 重點
- 功能：Markdown 渲染 + SVG fenced code block 雙重檢視（圖像 + 代碼）
- 輸入方式：直接貼 Markdown 或提供 CORS 啟用的 URL
- 應用場景：LLM 實驗日誌可視化（如 Opus 4.8 pelican 圖像生成日誌）

**原文：** [simon-willison](https://simonwillison.net/2026/May/28/markdown-svg-renderer/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tool: markdown-svg-renderer 
 A slightly customized Markdown rendering tool with special treatment for fenced code SVG blocks - it both renders the image and provides a tab for switching to the code view. 
 You can paste in Markdown or give it a URL to a CORS-enabled Markdown file or Gist. Here's an example where it loads a Markdown file full of LLM pelican logs for Opus 4.8 . 
 
 
 Tags: svg , tools , markdown , cors

</details>