---
id: inbox_8b39ac85
date: 2026-04-15
source_ref: "[[00-inbox/.../inbox_8b39ac85]]"
title: "datasette 1.0a27"
url: https://simonwillison.net/2026/Apr/15/datasette/#atom-everything
source: simon-willison
published_at: 2026-04-15T23:16:34+00:00
fetched_at: 2026-04-21T03:13:26.240488+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 1.0a27 推出多項重大變更。首先摒棄 Django 風格的 CSRF 表單令牌，改用現代瀏覽器標頭方式進行 CSRF 防護，參考 Filippo Valsorda 的相關說明。其次新增 RenameTableEvent 事件，當表格重新命名時會觸發，允許外掛程式對表格重新命名做出相應反應並同步相關資料。第三，datasette.client 方法新增 actor= 參數，支援以特定身份執行內部請求，這對編寫自動化測試特別有用。第四，新增 Database(is_temp_disk=True) 選項改進臨時資料庫處理，解決記憶體中資料庫導致的死鎖問題。此外，/upsert API 拒絕空主鍵值提升資料完整性，/database.json 端點新增 \"ok\": true 鍵確保一致性，call_with_supported_arguments() 正式列為公開 API。"
key_points:
  - "摒棄 Django 風格 CSRF 令牌，改用現代瀏覽器標頭提升安全性並簡化集成"
  - "新增 RenameTableEvent 和臨時磁碟資料庫選項，新增 actor= 參數支援身份模擬測試"
  - "提升 /upsert API 驗證、API 端點一致性和公開 API 文檔完整性"
tags: [datasette, security, api-changes, python, database]
topics: []
importance: 4
novelty: 4
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 1.0a27

Datasette 1.0a27 推出多項重大變更。首先摒棄 Django 風格的 CSRF 表單令牌，改用現代瀏覽器標頭方式進行 CSRF 防護，參考 Filippo Valsorda 的相關說明。其次新增 RenameTableEvent 事件，當表格重新命名時會觸發，允許外掛程式對表格重新命名做出相應反應並同步相關資料。第三，datasette.client 方法新增 actor= 參數，支援以特定身份執行內部請求，這對編寫自動化測試特別有用。第四，新增 Database(is_temp_disk=True) 選項改進臨時資料庫處理，解決記憶體中資料庫導致的死鎖問題。此外，/upsert API 拒絕空主鍵值提升資料完整性，/database.json 端點新增 "ok": true 鍵確保一致性，call_with_supported_arguments() 正式列為公開 API。

### 重點
- 摒棄 Django 風格 CSRF 令牌，改用現代瀏覽器標頭提升安全性並簡化集成
- 新增 RenameTableEvent 和臨時磁碟資料庫選項，新增 actor= 參數支援身份模擬測試
- 提升 /upsert API 驗證、API 端點一致性和公開 API 文檔完整性

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/15/datasette/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# datasette 1.0a27

<p><strong>Release:</strong> <a href="https://github.com/simonw/datasette/releases/tag/1.0a27">datasette 1.0a27</a></p>
    <p>Two major changes in this new Datasette alpha. I covered the first of those <a href="https://simonwillison.net/2026/Apr/14/replace-token-based-csrf/">in detail yesterday</a> - Datasette no longer uses Django-style CSRF form tokens, instead using modern browser headers <a href="https://words.filippo.io/csrf">as described by Filippo Valsorda</a>.</p>
<p>The second big change is that Datasette now fires a new <a href="https://docs.datasette.io/en/latest/events.html#datasette.events.RenameTableEvent">RenameTableEvent</a> any time a table is renamed during a SQLite transaction. This is useful because some plugins (like <a href="https://github.com/datasette/datasette-comments">datasette-comments</a>) attach additional data to table records by name, so a renamed table requires them to react in appropriate ways.</p>
<p>Here are the rest of the changes in the alpha:</p>
<blockquote>
<ul>
<li>New <a href="https://docs.datasette.io/en/latest/internals.html#internals-datasette-client-actor">actor= parameter</a> for <code>datasette.client</code> methods, allowing internal requests to be made as a specific actor. This is particularly useful for writing automated tests. (<a href="https://github.com/simonw/datasette/pull/2688">#2688</a>)</li>
<li>New <code>Database(is_temp_disk=True)</code> option, used internally for the internal database. This helps resolve intermittent database locked errors caused by the internal database being in-memory as opposed to on-disk. (<a href="https://github.com/simonw/datasette/issues/2683">#2683</a>) (<a href="https://github.com/simonw/datasette/pull/2684">#2684</a>)</li>
<li>The <code>/&lt;database&gt;/&lt;table&gt;/-/upsert</code> API (<a href="https://docs.datasette.io/en/latest/json_api.html#tableupsertview">docs</a>) now rejects rows with <code>null</code> primary key values. (<a href="https://github.com/simonw/datasette/issues/1936">#1936</a>)</li>
<li>Improved example in the API explorer for the <code>/-/upsert</code> endpoint (<a href="https://docs.datasette.io/en/latest/json_api.html#tableupsertview">docs</a>). (<a href="https://github.com/simonw/datasette/issues/1936">#1936</a>)</li>
<li>The <code>/&lt;database&gt;.json</code> endpoint now includes an <code>"ok": true</code> key, for consistency with other JSON API responses.</li>
<li><a href="https://docs.datasette.io/en/latest/internals.html#internals-utils-call-with-supported-arguments">call_with_supported_arguments()</a> is now documented as a supported public API. (<a href="https://github.com/simonw/datasette/pull/2678">#2678</a>)</li>
</ul>
</blockquote>
    
        <p>Tags: <a href="https://simonwillison.net/tags/annotated-release-notes">annotated-release-notes</a>, <a href="https://simonwillison.net/tags/datasette">datasette</a>, <a href="https://simonwillison.net/tags/python">python</a></p>

</details>