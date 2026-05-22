---
id: inbox_fc1826d8
date: 2026-05-14
source_ref: "[[00-inbox/2026-05-14/0036-simon-willison-datasette-agent-0-1a1-6b6f]]"
title: "datasette-agent 0.1a1"
url: https://simonwillison.net/2026/May/14/datasette-agent/#atom-everything
source: simon-willison
published_at: 2026-05-14T22:01:42+00:00
fetched_at: 2026-05-22T00:41:25.766758+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-agent 0.1a1 首次發布，引入 execute-sql 權限的應用。系統根據使用者的 execute-sql 權限決定向其展示哪些資料庫表。這是將細粒度權限檢查整合到代理工具決策流程的設計實踐。"
key_points:
  - "execute-sql permission 控制表格可見性，基於使用者權限展示不同資料集"
  - "權限檢查在代理工具初始化時執行，實現最小權限原則"
  - "首個 alpha 版本展示完整的權限驅動架構"
tags: [datasette-agent, permissions, least-privilege]
topics: [agents.mcp]
importance: 2
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-agent 0.1a1

datasette-agent 0.1a1 首次發布，引入 execute-sql 權限的應用。系統根據使用者的 execute-sql 權限決定向其展示哪些資料庫表。這是將細粒度權限檢查整合到代理工具決策流程的設計實踐。

### 重點
- execute-sql permission 控制表格可見性，基於使用者權限展示不同資料集
- 權限檢查在代理工具初始化時執行，實現最小權限原則
- 首個 alpha 版本展示完整的權限驅動架構

**原文：** [simon-willison](https://simonwillison.net/2026/May/14/datasette-agent/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-agent 0.1a1 
 
 
 Now uses the execute-sql permission when deciding which tables to list to the user. #8 
 
 
 
 
 Tags: datasette , datasette-agent

</details>