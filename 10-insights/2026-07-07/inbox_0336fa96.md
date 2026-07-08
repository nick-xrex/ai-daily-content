---
id: inbox_0336fa96
date: 2026-07-07
source_ref: "[[00-inbox/.../inbox_0336fa96]]"
title: "github-code Web Component"
url: https://simonwillison.net/2026/Jul/7/github-code-component/#atom-everything
source: simon-willison
published_at: 2026-07-07T16:18:16+00:00
fetched_at: 2026-07-08T01:03:27.948768+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 用 GPT-5.5 建立實驗性 Web Component（github-code），可直接嵌入 GitHub 代碼片段。該工具將 GitHub URLs 轉換為 raw.githubusercontent.com URLs，透過 fetch() 獲取目標文件並在指定行號範圍內顯示代碼（如 #L9-L18）。此組件無需外部依賴或伺服器端處理，為開發者提供輕量化的代碼展示解決方案，特別適合技術文檔或部落格中嵌入程式碼範例。展示了大型語言模型在實際前端工具開發中的應用。"
key_points:
  - "github-code Web Component 可從 GitHub URLs 直接抓取指定行號範圍的代碼並內嵌顯示"
  - "使用 fetch() 調用 raw.githubusercontent.com，無需伺服器端或外部 API，輕量化架構"
  - "由 GPT-5.5 一次 prompt 生成，展示 LLM 在 Web 元件開發中的實踐應用價值"
tags: [web-components, github-integration, developer-tools, gpt-5.5]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## github-code Web Component

Simon Willison 用 GPT-5.5 建立實驗性 Web Component（github-code），可直接嵌入 GitHub 代碼片段。該工具將 GitHub URLs 轉換為 raw.githubusercontent.com URLs，透過 fetch() 獲取目標文件並在指定行號範圍內顯示代碼（如 #L9-L18）。此組件無需外部依賴或伺服器端處理，為開發者提供輕量化的代碼展示解決方案，特別適合技術文檔或部落格中嵌入程式碼範例。展示了大型語言模型在實際前端工具開發中的應用。

### 重點
- github-code Web Component 可從 GitHub URLs 直接抓取指定行號範圍的代碼並內嵌顯示
- 使用 fetch() 調用 raw.githubusercontent.com，無需伺服器端或外部 API，輕量化架構
- 由 GPT-5.5 一次 prompt 生成，展示 LLM 在 Web 元件開發中的實踐應用價值

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/7/github-code-component/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# github-code Web Component

Tool: github-code Web Component 
 An experimental Web Component built using GPT-5.5 and the following prompt : 
 
 let's build a Web Component for embedding code from GitHub 
 &lt;github-code href="https://github.com/simonw/sqlite-ast/blob/437c759129154f05296324a7f82aa1246340dd14/sqlite_ast/parser.py#L9-L18"&gt;&lt;/github-code&gt; 
 It takes URLs like that, converts them to https://raw.githubusercontent.com/simonw/sqlite-ast/437c759129154f05296324a7f82aa1246340dd14/sqlite_ast/parser.py, then uses fetch() to fetch them and displays the specified range of lines - with line numbers, no syntax highlighting though 
 Show me a preview web browser so I can see your work 
 
 Here's what it looks like embedded on this page: 
 
 
 
 Tags: github , web-components , gpt

</details>