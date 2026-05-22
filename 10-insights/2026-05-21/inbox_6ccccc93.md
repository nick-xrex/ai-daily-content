---
id: inbox_6ccccc93
date: 2026-05-21
source_ref: "[[00-inbox/2026-05-21/0036-simon-willison-datasette-agent-0-1a3-77ec]]"
title: "datasette-agent 0.1a3"
url: https://simonwillison.net/2026/May/21/datasette-agent-2/#atom-everything
source: simon-willison
published_at: 2026-05-21T15:04:09+00:00
fetched_at: 2026-05-22T00:40:19.136365+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-agent 0.1a3 發布，改進代理推理過程顯示和結果集處理。新增「View SQL query」按鈕支援可見表和折疊查詢工具調用；過濾空推理 chunks 以減少噪音；改進截斷響應邏輯，確保表格結果仍對用戶可見。"
key_points:
  - "優化代理思考過程可視化，過濾空推理、新增查詢按鈕，降低用戶認知負荷"
  - "改進大型結果集截斷邏輯，保證資料完整性不因 token 限制而丟失"
tags: [datasette-agent, ux, result-handling, transparency]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-agent 0.1a3

datasette-agent 0.1a3 發布，改進代理推理過程顯示和結果集處理。新增「View SQL query」按鈕支援可見表和折疊查詢工具調用；過濾空推理 chunks 以減少噪音；改進截斷響應邏輯，確保表格結果仍對用戶可見。

### 重點
- 優化代理思考過程可視化，過濾空推理、新增查詢按鈕，降低用戶認知負荷
- 改進大型結果集截斷邏輯，保證資料完整性不因 token 限制而丟失

**原文：** [simon-willison](https://simonwillison.net/2026/May/21/datasette-agent-2/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-agent 0.1a3 
 
 
 "View SQL query" buttons for both visible tables and collapsed SQL result tool calls. 
 Don't display empty reasoning chunks 
 Improved handling of truncated responses - table still displays to the user even if the SQL results were truncated when showing the agent. 
 
 
 See Datasette Agent, an extensible AI assistant for Datasette . 
 
 
 Tags: datasette , datasette-agent

</details>