---
id: inbox_221f953b
date: 2026-04-20
source_ref: "[[00-inbox/.../inbox_221f953b]]"
title: "SQL functions in Google Sheets to fetch data from Datasette"
url: https://simonwillison.net/2026/Apr/20/datasette-sql/#atom-everything
source: simon-willison
published_at: 2026-04-20T02:33:58+00:00
fetched_at: 2026-04-21T03:09:37.420954+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 分享在 Google Sheets 中使用 SQL 函數從 Datasette 實例提取資料的方法。提供三種實現方式：（1）直接使用內建的 importdata() 函數無需認證；（2）用 named function 包裝 importdata()；（3）使用 Google Apps Script 以在 HTTP header 中發送 API token（importdata() 不支援此功能）。文章包含完整的可複製 Google Sheet 範例展示所有三種方法的具體實現，適合需要將外部資料整合入試算表的開發者。"
key_points:
  - "importdata() 函數可直接從 Datasette 查詢資料，無需額外認證"
  - "Google Apps Script 方法支援 API token 認證，突破 importdata() 的限制"
  - "提供完整的可複製 Google Sheet 範例展示所有三種方法"
tags: [datasette, google-sheets, sql, data-integration, google-apps-script]
topics: []
importance: 2
novelty: 2
deep_dive_candidate: false
deep_dive_approved: false
---

## SQL functions in Google Sheets to fetch data from Datasette

Simon Willison 分享在 Google Sheets 中使用 SQL 函數從 Datasette 實例提取資料的方法。提供三種實現方式：（1）直接使用內建的 importdata() 函數無需認證；（2）用 named function 包裝 importdata()；（3）使用 Google Apps Script 以在 HTTP header 中發送 API token（importdata() 不支援此功能）。文章包含完整的可複製 Google Sheet 範例展示所有三種方法的具體實現，適合需要將外部資料整合入試算表的開發者。

### 重點
- importdata() 函數可直接從 Datasette 查詢資料，無需額外認證
- Google Apps Script 方法支援 API token 認證，突破 importdata() 的限制
- 提供完整的可複製 Google Sheet 範例展示所有三種方法

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/20/datasette-sql/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# SQL functions in Google Sheets to fetch data from Datasette

<p><strong>TIL:</strong> <a href="https://til.simonwillison.net/google-sheets/datasette-sql">SQL functions in Google Sheets to fetch data from Datasette</a></p>
    <p>I put together some notes on patterns for fetching data from a Datasette instance directly into Google Sheets - using the <code>importdata()</code> function, a "named function" that wraps it or a Google Apps Script if you need to send an API token in an HTTP header (not supported by <code>importdata()</code>.)</p>
<p>Here's <a href="https://docs.google.com/spreadsheets/d/14lRV2-AeBmjI3lJbl2apwfC_ncXqL0uSV68lmtzUI7I/edit?gid=0#gid=0">an example sheet</a> demonstrating all three methods.</p>
    
        <p>Tags: <a href="https://simonwillison.net/tags/spreadsheets">spreadsheets</a>, <a href="https://simonwillison.net/tags/datasette">datasette</a>, <a href="https://simonwillison.net/tags/google">google</a></p>

</details>