---
id: inbox_08ffdcf4
date: 2026-05-29
source_ref: "[[00-inbox/2026-05-29/0216-simon-willison-datasette-1-0a31-7ce0]]"
title: "datasette 1.0a31"
url: https://simonwillison.net/2026/May/29/datasette/#atom-everything
source: simon-willison
published_at: 2026-05-29T03:32:02+00:00
fetched_at: 2026-05-30T02:25:00.429533+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette 1.0a31 新增兩項主要特性：SQL 寫入查詢執行能力，允許具權限使用者對資料庫執行 insert/update/delete 操作；儲存查詢功能（前稱 canned queries），支援私密儲存或與其他實例成員共享。演示展示模板化查詢介面，幫助使用者快速起手資料修改操作。"
key_points:
  - "SQL 寫入查詢：具權限使用者可執行 insert/update/delete，模板化介面降低門檻"
  - "儲存查詢（renamed from canned queries）：私密儲存或跨實例成員共享"
  - "Web-based SQL IDE 寫入能力 → 資料庫權限模型與用戶界面整合"
tags: [datasette, sql, sqlite, database-ui, write-queries]
topics: []
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 1.0a31

datasette 1.0a31 新增兩項主要特性：SQL 寫入查詢執行能力，允許具權限使用者對資料庫執行 insert/update/delete 操作；儲存查詢功能（前稱 canned queries），支援私密儲存或與其他實例成員共享。演示展示模板化查詢介面，幫助使用者快速起手資料修改操作。

### 重點
- SQL 寫入查詢：具權限使用者可執行 insert/update/delete，模板化介面降低門檻
- 儲存查詢（renamed from canned queries）：私密儲存或跨實例成員共享
- Web-based SQL IDE 寫入能力 → 資料庫權限模型與用戶界面整合

**原文：** [simon-willison](https://simonwillison.net/2026/May/29/datasette/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette 1.0a31 
 Another significant alpha release, with two new headline features. 
 
 Datasette now offers users with the necessary permissions the ability to both execute write queries against their database and to save stored queries (renamed from "canned queries") both privately and for use by other members of their Datasette instance. 
 
 There's more detail in SQL write queries and stored queries in Datasette 1.0a31 on the Datasette blog, which now has three posts introducing new features since the blog launched two weeks ago. 
 Here's an animated demo from the blog post showing how the new execute query interface lets people get started with templated insert/update/delete queries from tables they have permission to edit: 
 
 
 
 Tags: projects , sql , sqlite , datasette , annotated-release-notes

</details>