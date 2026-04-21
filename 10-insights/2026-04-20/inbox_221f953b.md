---
id: inbox_221f953b
date: 2026-04-20
source_ref: "[[00-inbox/.../inbox_221f953b]]"
title: "SQL functions in Google Sheets to fetch data from Datasette"
url: https://simonwillison.net/2026/Apr/20/datasette-sql/#atom-everything
source: (resumed)
published_at: 2026-04-20T02:33:58+00:00
fetched_at: 2026-04-21T02:34:53.647896+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 分享了从 Datasette 实例直接将数据获取到 Google Sheets 的三种方法。首先可以使用原生的 `importdata()` 函数，其次可以用「named function」进行包装，第三种方法是通过 Google Apps Script 在 HTTP header 中发送 API token（importdata() 不支持此功能）。这对需要定期将数据库内容同步到 spreadsheet 的数据工作流很有用。文章附带了完整示例 sheet。"
key_points:
  - "使用 importdata() 函数直接从 Datasette 获取数据到 Google Sheets"
  - "通过 named function 包装简化调用流程"
  - "使用 Google Apps Script 处理需要 HTTP header 认证的场景"
tags: [datasette, google-sheets, data-integration, sql]
topics: []
importance: 2
novelty: 2
deep_dive_candidate: false
deep_dive_approved: false
---

## SQL functions in Google Sheets to fetch data from Datasette

Simon Willison 分享了从 Datasette 实例直接将数据获取到 Google Sheets 的三种方法。首先可以使用原生的 `importdata()` 函数，其次可以用「named function」进行包装，第三种方法是通过 Google Apps Script 在 HTTP header 中发送 API token（importdata() 不支持此功能）。这对需要定期将数据库内容同步到 spreadsheet 的数据工作流很有用。文章附带了完整示例 sheet。

### 重點
- 使用 importdata() 函数直接从 Datasette 获取数据到 Google Sheets
- 通过 named function 包装简化调用流程
- 使用 Google Apps Script 处理需要 HTTP header 认证的场景

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/20/datasette-sql/#atom-everything)