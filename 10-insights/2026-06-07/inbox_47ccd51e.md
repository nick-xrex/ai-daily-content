---
id: inbox_47ccd51e
date: 2026-06-07
source_ref: "[[00-inbox/2026-06-07/1800-simon-willison-datasette-agent-edit-0-1a0-d8cb]]"
title: "datasette-agent-edit 0.1a0"
url: https://simonwillison.net/2026/Jun/7/datasette-agent-edit/#atom-everything
source: simon-willison
published_at: 2026-06-07T23:56:38+00:00
fetched_at: 2026-06-08T18:09:47.571288+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 發佈 datasette-agent-edit 0.1a0 版本，這是一個為 Datasette 平台設計的插件框架。該框架專為需要進行文本編輯的 agentic 應用而建，支持協作 Markdown 編輯、大型 SQL 查詢更新和 SVG 文件編輯等場景。核心設計實現了三個工具：view 用於檢視指定範圍的文本（帶行號），str_replace 用於精確字符串替換（要求唯一匹配），insert 用於在指定行號後插入文本。這三個工具直接參考 Claude text editor 的經驗設計。該框架的目標是提供統一的 API，讓不同的 Datasette 插件無需重複實現相同的編輯工具邏輯。"
key_points:
  - "三個核心工具：view（帶行號）、str_replace（精確替換）、insert（指定行後插入），直接移植自 Claude text editor 設計"
  - "支持 Markdown、SQL、SVG 等多種文本型資料的 agentic 編輯"
  - "統一的 Datasette Agent 插件框架，減少重複實現"
tags: [datasette, llm-tool-use, agent-editing, text-tools]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: true
deep_dive_approved: false
---

## datasette-agent-edit 0.1a0

Simon Willison 發佈 datasette-agent-edit 0.1a0 版本，這是一個為 Datasette 平台設計的插件框架。該框架專為需要進行文本編輯的 agentic 應用而建，支持協作 Markdown 編輯、大型 SQL 查詢更新和 SVG 文件編輯等場景。核心設計實現了三個工具：view 用於檢視指定範圍的文本（帶行號），str_replace 用於精確字符串替換（要求唯一匹配），insert 用於在指定行號後插入文本。這三個工具直接參考 Claude text editor 的經驗設計。該框架的目標是提供統一的 API，讓不同的 Datasette 插件無需重複實現相同的編輯工具邏輯。

### 重點
- 三個核心工具：view（帶行號）、str_replace（精確替換）、insert（指定行後插入），直接移植自 Claude text editor 設計
- 支持 Markdown、SQL、SVG 等多種文本型資料的 agentic 編輯
- 統一的 Datasette Agent 插件框架，減少重複實現

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/7/datasette-agent-edit/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-agent-edit 0.1a0 
 I'm planning several plugins for Datasette Agent which can make edits to existing pieces of text - things like collaborative Markdown editing, updating large SQL queries, and editing SVG files. 
 Agentic editing of text is a little tricky to get right. My favorite published design for this is for the Claude text editor , which implements the following tools: 
 
 view - view sections of a file, with line numbers added to every line. 
 str_replace - find an exact old_str and replace it with new_str - fail if the original string is not unique 
 insert - insert the specified text after the specified line number 
 
 Rather than recreate these patterns for every plugin that needs them I decided to create this base plugin, datasette-agent-edit , which implements the core tools in a way that allows them to be adapted for other plugins. 
 
 
 Tags: ai , datasette , generative-ai , llms , llm-tool-use , datasette-agent

</details>