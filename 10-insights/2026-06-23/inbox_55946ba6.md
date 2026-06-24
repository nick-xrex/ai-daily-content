---
id: inbox_55946ba6
date: 2026-06-23
source_ref: "[[00-inbox/2026-06-23/2200-simon-willison-datasette-1-0a35-c5a8]]"
title: "datasette 1.0a35"
url: https://simonwillison.net/2026/Jun/23/datasette/#atom-everything
source: simon-willison
published_at: 2026-06-23T21:34:37+00:00
fetched_at: 2026-06-24T22:08:34.908513+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 1.0a35 發布重大版本，引入三項核心功能。新增「Create table」介面與 /<database>/-/create JSON API，支援定義 columns、primary keys、custom column types、NOT NULL constraints、literal/expression defaults 及 single-column foreign keys（PR #2787）。新增「Alter table」表格動作與 /<database>/<table>/-/alter JSON API，允許 add/rename/reorder/drop columns、變更 column types/defaults/constraints/primary keys/foreign keys、重命名表格，並內含「Drop table」按鈕（PR #2788）。新增 Template context documentation，列舉自定義模板可用變數並作為穩定 API 至 Datasette 2.0，文檔由 dataclass 定義自動生成並配有測試驗證（PR #1510、#2127、#1477、#2803）。"
key_points:
  - "Create/Alter table 完整支持 schema 變更：columns/types/constraints/foreign keys，均暴露 JSON API"
  - "Template context documentation 以 dataclass 自動生成，配有測試驗證，確保模板 API 穩定性"
  - "三個互相關聯的大功能一併推出，大幅提升 Datasette 的自託管數據庫管理能力"
tags: [datasette, schema-management, database-ui, json-api]
topics: []
importance: 3
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 1.0a35

Datasette 1.0a35 發布重大版本，引入三項核心功能。新增「Create table」介面與 /<database>/-/create JSON API，支援定義 columns、primary keys、custom column types、NOT NULL constraints、literal/expression defaults 及 single-column foreign keys（PR #2787）。新增「Alter table」表格動作與 /<database>/<table>/-/alter JSON API，允許 add/rename/reorder/drop columns、變更 column types/defaults/constraints/primary keys/foreign keys、重命名表格，並內含「Drop table」按鈕（PR #2788）。新增 Template context documentation，列舉自定義模板可用變數並作為穩定 API 至 Datasette 2.0，文檔由 dataclass 定義自動生成並配有測試驗證（PR #1510、#2127、#1477、#2803）。

### 重點
- Create/Alter table 完整支持 schema 變更：columns/types/constraints/foreign keys，均暴露 JSON API
- Template context documentation 以 dataclass 自動生成，配有測試驗證，確保模板 API 穩定性
- 三個互相關聯的大功能一併推出，大幅提升 Datasette 的自託管數據庫管理能力

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/23/datasette/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette 1.0a35 
 I'll write more about this one soon, but it's a big release. Three highlights from the release notes: 
 
 
 New "Create table" interface in the database actions menu, backed by the /&lt;database&gt;/-/create JSON API . It can define columns, primary keys, custom column types, NOT NULL constraints, literal defaults, expression defaults and single-column foreign keys. ( #2787 ) 
 New "Alter table" table action and /&lt;database&gt;/&lt;table&gt;/-/alter JSON API for changing existing tables: add, rename, reorder and drop columns; change column types, defaults, NOT NULL constraints, primary keys and foreign keys; and rename the table. The alter table dialog also includes a "Drop table" button. ( #2788 ) 
 New Template context documentation listing the variables available to custom templates for Datasette's core pages. Variables documented there are treated as a stable API for custom templates until Datasette 2.0. The documentation is generated from dataclass definitions next to the view code, with tests that compare the documented fields against the actual contexts rendered by the database, table, query and row pages. ( #1510 , #2127 , #1477 , #2803 ) 
 
 
 Here's a rough video demo I made of the new create/alter table feature as part of reviewing the PR : 
 
 
 
 
 
 
 Tags: datasette

</details>