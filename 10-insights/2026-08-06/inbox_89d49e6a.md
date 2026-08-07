---
id: inbox_89d49e6a
date: 2026-08-06
source_ref: "[[00-inbox/.../inbox_89d49e6a]]"
title: "datasette 0.65.3"
url: https://simonwillison.net/2026/Aug/6/datasette-2/#atom-everything
source: simon-willison
published_at: 2026-08-06T18:22:07+00:00
fetched_at: 2026-08-07T01:24:19.584633+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 0.65.3 穩定版本回溯了 1.0a38 中修復的 SQL 注入安全漏洞。此漏洞影響同一資料庫混合公開與私有表格的配置，允許具有公開表格存取的使用者執行 SQL 注入以存取私有表格。回溯版本為不願升級至 alpha 版本的穩定版使用者提供安全補丁。"
key_points:
  - "Datasette 0.65.3 包含 SQL 注入漏洞修正的回溯，影響同資料庫公開私有表格混合配置"
tags: [security, backport, datasette]
topics: []
importance: 4
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 0.65.3

Datasette 0.65.3 穩定版本回溯了 1.0a38 中修復的 SQL 注入安全漏洞。此漏洞影響同一資料庫混合公開與私有表格的配置，允許具有公開表格存取的使用者執行 SQL 注入以存取私有表格。回溯版本為不願升級至 alpha 版本的穩定版使用者提供安全補丁。

### 重點
- Datasette 0.65.3 包含 SQL 注入漏洞修正的回溯，影響同資料庫公開私有表格混合配置

**原文：** [simon-willison](https://simonwillison.net/2026/Aug/6/datasette-2/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# datasette 0.65.3

Release: datasette 0.65.3 
 Back-ported the SQL Injection security fix from 1.0a38 . 
 
 
 Tags: datasette

</details>