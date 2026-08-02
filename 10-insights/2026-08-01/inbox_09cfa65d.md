---
id: inbox_09cfa65d
date: 2026-08-01
source_ref: "[[00-inbox/.../inbox_09cfa65d]]"
title: "datasette-apps 0.2a0"
url: https://simonwillison.net/2026/Aug/1/datasette-apps/#atom-everything
source: simon-willison
published_at: 2026-08-01T21:23:56+00:00
fetched_at: 2026-08-02T03:39:09.761098+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-apps 0.2a0 發布，重點改進與 Datasette Agent 的協作能力。新增兩項工具：(1) app_debug()，允許 agent 隱形打開應用（透過 opacity:0 + pointer-events:none iframe）並用 JavaScript 進行測試、測量元素尺寸；(2) app_list()，讓 agent 列出用戶有權編輯的應用。app_debug() 基於 datasette-agent 0.4a0 引入的 context.browser_task() 機制實現，提供沙盒隔離的 JavaScript 執行環境。此設計使 agent 能安全地進行應用煙測與自動化驗證。"
key_points:
  - "app_debug() 工具用 opacity:0 + pointer-events:none iframe 實現隱形沙盒測試，agent 可執行 JavaScript 並測量元素"
  - "app_list() 工具讓 agent 發現有編輯權限的應用清單"
  - "基於 datasette-agent 0.4a0 的 context.browser_task() 沙盒機制"
tags: [datasette, datasette-apps, agent-tools, javascript-sandbox, browser-automation]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-apps 0.2a0

datasette-apps 0.2a0 發布，重點改進與 Datasette Agent 的協作能力。新增兩項工具：(1) app_debug()，允許 agent 隱形打開應用（透過 opacity:0 + pointer-events:none iframe）並用 JavaScript 進行測試、測量元素尺寸；(2) app_list()，讓 agent 列出用戶有權編輯的應用。app_debug() 基於 datasette-agent 0.4a0 引入的 context.browser_task() 機制實現，提供沙盒隔離的 JavaScript 執行環境。此設計使 agent 能安全地進行應用煙測與自動化驗證。

### 重點
- app_debug() 工具用 opacity:0 + pointer-events:none iframe 實現隱形沙盒測試，agent 可執行 JavaScript 並測量元素
- app_list() 工具讓 agent 發現有編輯權限的應用清單
- 基於 datasette-agent 0.4a0 的 context.browser_task() 沙盒機制

**原文：** [simon-willison](https://simonwillison.net/2026/Aug/1/datasette-apps/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# datasette-apps 0.2a0

Release: datasette-apps 0.2a0 
 
 Changes that improve Datasette Apps when created and edited using Datasette Agent : 
 
 New app_debug() tool allowing agent to open an app (invisibly) and test it using JavaScript. #33 
 New app_list() tool for listing apps the user has permission to edit, so the agent can edit them. #36 
 
 
 The app_debug() tool is pretty neat: it works by displaying the app in a opacity: 0 iframe with pointer-events: none (so it can't be seen or interacted with) and then executing agent-provided JavaScript inside that sandboxed iframe. This means the agent can smoke test that the app is working and even do things like measure the dimensions of different elements. 
 This uses the new context.browser_task() mechanism added in datasette-agent 0.4a0 . 
 
 
 Tags: iframes , datasette , datasette-apps

</details>