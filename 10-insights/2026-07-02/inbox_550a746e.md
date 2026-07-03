---
id: inbox_550a746e
date: 2026-07-02
source_ref: "[[00-inbox/2026-07-02/2200-simon-willison-using-dspy-to-evaluate-and-improve-datas-4b96]]"
title: "Using DSPy to evaluate and improve Datasette Agent&#39;s SQL system prompts"
url: https://simonwillison.net/2026/Jul/2/dspy-datasette-agent-prompts/#atom-everything
source: simon-willison
published_at: 2026-07-02T18:25:00+00:00
fetched_at: 2026-07-02T22:08:35.663789+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 使用 Claude Fable 5 在 Claude Code 中執行研究任務，以 DSPy 框架評估和改進 Datasette Agent 的 SQL 系統提示。測試採用 GPT-4.1 mini 與 nano，發現關鍵改進方向：schema 列表應包含具體列名而非僅表名，以防止 AI 在缺乏列名時陷入猜測（如 page_count、order_id）與錯誤重試迴圈。此發現對優化任何執行結構化查詢的代理系統提示具有通用啟示。"
key_points:
  - "DSPy 框架可系統性評估並改進 AI 系統提示的有效性"
  - "Schema 定義需包含列名清單，否則導致代理猜測列名與錯誤重試迴圈"
  - "Claude Fable 5 支援非同步研究任務的複雜工程工作"
tags: [dspy, datasette-agent, system-prompts, prompt-optimization, sql]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Using DSPy to evaluate and improve Datasette Agent's SQL system prompts

Simon Willison 使用 Claude Fable 5 在 Claude Code 中執行研究任務，以 DSPy 框架評估和改進 Datasette Agent 的 SQL 系統提示。測試採用 GPT-4.1 mini 與 nano，發現關鍵改進方向：schema 列表應包含具體列名而非僅表名，以防止 AI 在缺乏列名時陷入猜測（如 page_count、order_id）與錯誤重試迴圈。此發現對優化任何執行結構化查詢的代理系統提示具有通用啟示。

### 重點
- DSPy 框架可系統性評估並改進 AI 系統提示的有效性
- Schema 定義需包含列名清單，否則導致代理猜測列名與錯誤重試迴圈
- Claude Fable 5 支援非同步研究任務的複雜工程工作

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/2/dspy-datasette-agent-prompts/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Research: Using DSPy to evaluate and improve Datasette Agent&#x27;s SQL system prompts 
 One of this morning's AIE keynotes covered dspy , which reminded me I've been meaning to see if it could help me improve the system prompt used by Datasette Agent - so I fired off an asynchronous research task in Claude Code for web using Claude Fable 5: 
 
 Pip install the latest Datasette alpha and datasette-agent and dspy - then figure out how to use dspy to evaluate and improve the main system prompts used by Datasette Agent for the feature where it can execute read only SQL queries to answer user questions about data. 
 
 Fable chose to test using GPT 4.1 mini and nano, and identified several promising looking directions for improvements. I particularly like this one: 
 
 The schema listing gives only table names; the "don't call describe_table if you already have the information" advice caused column-name guessing (page_count, o.order_id, first_name) and error-retry loops in baseline traces. Either include column names in the prompt's schema listing or soften that advice. 
 
 
 
 Tags: ai , datasette , generative-ai , llms , evals , dspy , datasette-agent , claude-mythos

</details>