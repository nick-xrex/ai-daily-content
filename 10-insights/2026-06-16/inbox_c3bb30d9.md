---
id: inbox_c3bb30d9
date: 2026-06-16
source_ref: "[[00-inbox/2026-06-16/2200-simon-willison-datasette-1-0a34-c560]]"
title: "datasette 1.0a34"
url: https://simonwillison.net/2026/Jun/16/datasette/#atom-everything
source: simon-willison
published_at: 2026-06-16T21:31:24+00:00
fetched_at: 2026-06-17T22:05:50.516351+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 1.0a34 alpha 版本發布，新增的主要功能是在 Datasette 界面內直接插入、編輯和刪除資料表中的行記錄。這些功能在表格頁面的工具欄中可用，編輯和刪除操作也可作為行詳細頁面上的 action items 使用。此功能的靈感來自 Datasette Agent，它已支持通過自然語言對話修改資料。這個對比暴露了一個問題：用戶可以通過 Agent 對話界面執行 SQL 寫操作，卻無法在主 Datasette UI 中進行，體驗不夠一致。新的行級 CRUD 功能彌補了這一長期缺失的功能，使 Datasette 成為更完整的資料管理工具。"
key_points:
  - "Datasette 1.0a34 新增行級 CRUD 操作（插入、編輯、刪除），在表格頁面和行詳細頁可用"
  - "設計靈感：Datasette Agent 已支持 SQL 寫入，凸顯了主 UI 的功能空白"
  - "改進意義：統一多端操作體驗，讓 Datasette 成為完整的資料庫 UI"
tags: [datasette, row-editing, database-ui, crud-operations, alpha-release]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 1.0a34

Datasette 1.0a34 alpha 版本發布，新增的主要功能是在 Datasette 界面內直接插入、編輯和刪除資料表中的行記錄。這些功能在表格頁面的工具欄中可用，編輯和刪除操作也可作為行詳細頁面上的 action items 使用。此功能的靈感來自 Datasette Agent，它已支持通過自然語言對話修改資料。這個對比暴露了一個問題：用戶可以通過 Agent 對話界面執行 SQL 寫操作，卻無法在主 Datasette UI 中進行，體驗不夠一致。新的行級 CRUD 功能彌補了這一長期缺失的功能，使 Datasette 成為更完整的資料管理工具。

### 重點
- Datasette 1.0a34 新增行級 CRUD 操作（插入、編輯、刪除），在表格頁面和行詳細頁可用
- 設計靈感：Datasette Agent 已支持 SQL 寫入，凸顯了主 UI 的功能空白
- 改進意義：統一多端操作體驗，讓 Datasette 成為完整的資料庫 UI

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/16/datasette/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette 1.0a34 
 Quoting the release notes: 
 
 The big feature in this alpha is tools to insert, edit and delete rows within the Datasette interface. These features are available on table pages, and edit and delete are also available as action items on the row page. 
 
 

 The inspiration for this feature - which is long overdue - was Datasette Agent . I added SQL write support to that the other day which highlighted how absurd it was that you could insert and edit ties via the chat interface but not in the regular Datasette UI! 
 
 
 Tags: projects , datasette , annotated-release-notes

</details>