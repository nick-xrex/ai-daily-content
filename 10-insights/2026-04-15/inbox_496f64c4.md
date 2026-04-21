---
id: inbox_496f64c4
date: 2026-04-15
source_ref: "[[00-inbox/.../inbox_496f64c4]]"
title: "datasette-export-database 0.3a1"
url: https://simonwillison.net/2026/Apr/15/datasette-export-database/#atom-everything
source: simon-willison
published_at: 2026-04-15T23:52:35+00:00
fetched_at: 2026-04-21T03:13:26.237397+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-export-database 0.3a1 發布，此次更新是為了適應 Datasette 1.0a27 引入的 CSRF 安全性變更。該外掛程式原本使用 ds_csrftoken cookie 作為自訂簽名 URL 的一部分。但 Datasette 1.0a27 引入了重大變更，不再設置此 cookie，改用現代瀏覽器標頭的 CSRF 防護方式。因此依賴舊 CSRF 機制的外掛程式都需要升級。datasette-export-database 的此版本更新就是為了實現這個相容性。"
key_points:
  - "適應 Datasette 1.0a27 的 CSRF 保護機制變更"
  - "更新外掛程式以移除對已棄用 ds_csrftoken cookie 的依賴"
  - "Datasette 1.0a27 改用現代瀏覽器標頭進行 CSRF 防護"
tags: [datasette, plugin, maintenance-release]
topics: []
importance: 1
novelty: 1
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-export-database 0.3a1

datasette-export-database 0.3a1 發布，此次更新是為了適應 Datasette 1.0a27 引入的 CSRF 安全性變更。該外掛程式原本使用 ds_csrftoken cookie 作為自訂簽名 URL 的一部分。但 Datasette 1.0a27 引入了重大變更，不再設置此 cookie，改用現代瀏覽器標頭的 CSRF 防護方式。因此依賴舊 CSRF 機制的外掛程式都需要升級。datasette-export-database 的此版本更新就是為了實現這個相容性。

### 重點
- 適應 Datasette 1.0a27 的 CSRF 保護機制變更
- 更新外掛程式以移除對已棄用 ds_csrftoken cookie 的依賴
- Datasette 1.0a27 改用現代瀏覽器標頭進行 CSRF 防護

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/15/datasette-export-database/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# datasette-export-database 0.3a1

<p><strong>Release:</strong> <a href="https://github.com/datasette/datasette-export-database/releases/tag/0.3a1">datasette-export-database 0.3a1</a></p>
    <p>This plugin was using the <code>ds_csrftoken</code> cookie as part of a custom signed URL, which needed upgrading now that Datasette 1.0a27 <a href="https://simonwillison.net/2026/Apr/14/replace-token-based-csrf/">no longer sets that cookie</a>.</p>
    
        <p>Tags: <a href="https://simonwillison.net/tags/datasette">datasette</a></p>

</details>