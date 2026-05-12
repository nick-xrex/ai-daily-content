---
id: inbox_3aa59e90
date: 2026-05-11
source_ref: "[[00-inbox/.../inbox_3aa59e90]]"
title: "Markdown browser for LLMs"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t9tsro/markdown_browser_for_llms/
source: reddit-localllama
published_at: 2026-05-11T05:23:15+00:00
fetched_at: 2026-05-12T01:39:55.207094+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者推出 TextWeb，為 AI agents 設計的 Markdown 網頁渲染器，以 Markdown 文本代替昂貴的視覺截圖，直接降低推理成本。支援完整 JavaScript 執行、互動元素標註、導航、滾動、文本輸入及按鈕點擊等操作。提供 CLI 和 MCP 服務器兩種使用方式，可與 llama.cpp web UI 直接整合。"
key_points:
  - "Markdown 渲染替代視覺截圖，大幅降低 LLM agent 視覺推理成本"
  - "完整的 JavaScript 執行和互動元素標註支援"
  - "提供 MCP 服務器，可與 llama.cpp 和其他 LLM 框架整合"
tags: [textweb, markdown-rendering, mcp-server, agent-tools, local-llm]
topics: [agents.mcp]
importance: 4
novelty: 5
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Markdown browser for LLMs

開發者推出 TextWeb，為 AI agents 設計的 Markdown 網頁渲染器，以 Markdown 文本代替昂貴的視覺截圖，直接降低推理成本。支援完整 JavaScript 執行、互動元素標註、導航、滾動、文本輸入及按鈕點擊等操作。提供 CLI 和 MCP 服務器兩種使用方式，可與 llama.cpp web UI 直接整合。

### 重點
- Markdown 渲染替代視覺截圖，大幅降低 LLM agent 視覺推理成本
- 完整的 JavaScript 執行和互動元素標註支援
- 提供 MCP 服務器，可與 llama.cpp 和其他 LLM 框架整合

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t9tsro/markdown_browser_for_llms/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Markdown browser for LLMs

I built a markdown web renderer for AI agents. Instead of taking expensive screenshots and piping them through vision models, TextWeb renders web pages as markdown that LLMs can reason about natively. Full JavaScript execution, interactive elements annotated. It provides a CLI and an MCP server. You can find it here: https://github.com/woheller69/textweb The LLM can do things like: navigate a web page, scroll up/down, enter text into input fields, click buttons, etc. Works with llama.cpp web UI. It is based on https://github.com/chrisrobison/textweb which has a text grid renderer instead of markdown. &#32; submitted by &#32; /u/DocWolle [link] &#32; [comments]

</details>