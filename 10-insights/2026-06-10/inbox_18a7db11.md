---
id: inbox_18a7db11
date: 2026-06-10
source_ref: "[[00-inbox/2026-06-10/2200-simon-willison-datasette-agent-0-2a0-8d15]]"
title: "datasette-agent 0.2a0"
url: https://simonwillison.net/2026/Jun/10/datasette-agent/#atom-everything
source: simon-willison
published_at: 2026-06-10T23:57:27+00:00
fetched_at: 2026-06-11T22:08:02.453592+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-agent 发布 0.2a0 版本，新增两项交互式 agent 特性。首先，tools 可通过 ToolContext.ask_user() 在执行中向用户提问（支持 yes/no、多选或自由文本），提问会暂停对话并持久化到数据库，重启后能恢复——工具会重新执行并重放已保存的答案。其次，新增 save_query 内置 tool，让 agent 提议保存 SQL 为 Datasette stored query，需用户明确批准后才持久化。两项功能由 Claude Fable 5 协助实现。"
key_points:
  - "Tools 可通过 ToolContext.ask_user() 实现对话中提问（yes/no、options=[]、free_text=True），问题持久化至数据库且支持恢复"
  - "新增 save_query tool 让 agent 建议保存 SQL，需人工审批才写入以防副作用"
  - "使用 Claude Fable 5 实现交互式 agent 模式，验证新 LLM alpha 的可行性"
tags: [datasette-agent, llm-agents, interactive-tools, sql, claude-fable]
topics: [foundation_models.claude]
importance: 2
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-agent 0.2a0

datasette-agent 发布 0.2a0 版本，新增两项交互式 agent 特性。首先，tools 可通过 ToolContext.ask_user() 在执行中向用户提问（支持 yes/no、多选或自由文本），提问会暂停对话并持久化到数据库，重启后能恢复——工具会重新执行并重放已保存的答案。其次，新增 save_query 内置 tool，让 agent 提议保存 SQL 为 Datasette stored query，需用户明确批准后才持久化。两项功能由 Claude Fable 5 协助实现。

### 重點
- Tools 可通过 ToolContext.ask_user() 实现对话中提问（yes/no、options=[]、free_text=True），问题持久化至数据库且支持恢复
- 新增 save_query tool 让 agent 建议保存 SQL，需人工审批才写入以防副作用
- 使用 Claude Fable 5 实现交互式 agent 模式，验证新 LLM alpha 的可行性

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/10/datasette-agent/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-agent 0.2a0 
 Highlights from the release notes: 
 
 
 Tools can now ask the user questions mid-execution. Tools that declare a context parameter receive a ToolContext object, and await context.ask_user(...) can ask a yes/no, multiple-choice ( options=[...] ) or free-text ( free_text=True ) question. While a question is unanswered the agent turn suspends: the question renders as a form in the chat UI and persists to the internal database, so suspended conversations survive a server restart. Once answered, the tool re-executes from the top with stored answers replayed, so call ask_user() before performing side effects. #20 
 New built-in save_query tool: the agent can save SQL it has written as a Datasette stored query . Saving always requires human approval - the agent shows the full SQL plus the proposed name, database and visibility, and nothing is stored until you click Yes. #20 
 
 
 The ask_user() feature was enabled by the new LLM alpha I built yesterday with the help of Claude Fable 5. 
 
 
 Tags: ai , datasette , generative-ai , llms , datasette-agent

</details>