---
id: inbox_9ce7b755
date: 2026-04-14
source_ref: "[[00-inbox/.../inbox_9ce7b755]]"
title: "datasette PR #2689: Replace token-based CSRF with Sec-Fetch-Site header protection"
url: https://simonwillison.net/2026/Apr/14/replace-token-based-csrf/#atom-everything
source: (resumed)
published_at: 2026-04-14T23:58:53+00:00
fetched_at: 2026-04-21T02:40:32.031859+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 框架更新了跨站請求偽造（CSRF）防護機制，從基於 Token 的方案改用 Sec-Fetch-Site 請求頭檢驗。這套方法參考 Go 1.25 及 Filippo Valsorda 的資安研究。新方案移除了模板中所有隱藏 CSRF Token 的 input 標籤，廢棄了原有的 `skip_csrf` 外掛鉤點，簡化開發者體驗。該 PR 由 Claude Code 在人工密切指導下完成共 10 個 commit。官方文件已更新升級指南。"
key_points:
  - "Sec-Fetch-Site 請求頭取代 Token 式防護，移除所有 `<input type=\"hidden\" name=\"csrftoken\">` 標籤"
  - "廢棄 skip_csrf 外掛鉤點，統一安全策略實作"
  - "Claude Code 輔助開發，人工複審把關，10 個 commit 重構完成"
tags: [csrf-protection, web-security, datasette, sec-fetch-site, ai-assisted]
topics: []
importance: 3
novelty: 2
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette PR #2689: Replace token-based CSRF with Sec-Fetch-Site header protection

Datasette 框架更新了跨站請求偽造（CSRF）防護機制，從基於 Token 的方案改用 Sec-Fetch-Site 請求頭檢驗。這套方法參考 Go 1.25 及 Filippo Valsorda 的資安研究。新方案移除了模板中所有隱藏 CSRF Token 的 input 標籤，廢棄了原有的 `skip_csrf` 外掛鉤點，簡化開發者體驗。該 PR 由 Claude Code 在人工密切指導下完成共 10 個 commit。官方文件已更新升級指南。

### 重點
- Sec-Fetch-Site 請求頭取代 Token 式防護，移除所有 `<input type="hidden" name="csrftoken">` 標籤
- 廢棄 skip_csrf 外掛鉤點，統一安全策略實作
- Claude Code 輔助開發，人工複審把關，10 個 commit 重構完成

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/14/replace-token-based-csrf/#atom-everything)