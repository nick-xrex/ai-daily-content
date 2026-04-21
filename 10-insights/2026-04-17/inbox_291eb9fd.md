---
id: inbox_291eb9fd
date: 2026-04-17
source_ref: "[[00-inbox/.../inbox_291eb9fd]]"
title: "datasette 1.0a28"
url: https://simonwillison.net/2026/Apr/17/datasette/#atom-everything
source: simon-willison
published_at: 2026-04-17T04:01:56+00:00
fetched_at: 2026-04-21T03:13:26.209881+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 1.0a28 發布，主要修復了 1.0a27 版本引入的多個相容性問題。修正了 execute_write_fn() 回調函式的參數名稱相容性錯誤，新增了 database.close() 方法以同時關閉寫入連線，以及新增 datasette.close() 方法用於完整清理資料庫和相關資源。另外新增 pytest 外掛程式可自動清理測試中的臨時 Datasette 實例，避免在編寫大量外掛程式測試時耗盡檔案描述符。此版本的主要變更使用 Claude Code 和新發布的 Claude Opus 4.7 實現。"
key_points:
  - "修復 execute_write_fn() 回調函式的相容性錯誤（issue #2691）"
  - "新增 datasette.close() 方法和自動清理 pytest 外掛程式以防止資源洩漏"
  - "使用 Claude Code 和 Claude Opus 4.7 實現版本變更"
tags: [datasette, bug-fix, python, claude-code]
topics: [foundation_models.claude]
importance: 3
novelty: 2
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 1.0a28

Datasette 1.0a28 發布，主要修復了 1.0a27 版本引入的多個相容性問題。修正了 execute_write_fn() 回調函式的參數名稱相容性錯誤，新增了 database.close() 方法以同時關閉寫入連線，以及新增 datasette.close() 方法用於完整清理資料庫和相關資源。另外新增 pytest 外掛程式可自動清理測試中的臨時 Datasette 實例，避免在編寫大量外掛程式測試時耗盡檔案描述符。此版本的主要變更使用 Claude Code 和新發布的 Claude Opus 4.7 實現。

### 重點
- 修復 execute_write_fn() 回調函式的相容性錯誤（issue #2691）
- 新增 datasette.close() 方法和自動清理 pytest 外掛程式以防止資源洩漏
- 使用 Claude Code 和 Claude Opus 4.7 實現版本變更

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/17/datasette/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# datasette 1.0a28

<p><strong>Release:</strong> <a href="https://github.com/simonw/datasette/releases/tag/1.0a28">datasette 1.0a28</a></p>
    <p>I was upgrading Datasette Cloud to <a href="https://simonwillison.net/2026/Apr/15/datasette/">1.0a27</a> and discovered a nasty collection of accidental breakages caused by changes in that alpha. This new alpha addresses those directly:</p>
<blockquote>
<ul>
<li>Fixed a compatibility bug introduced in 1.0a27 where <code>execute_write_fn()</code> callbacks with a parameter name other than <code>conn</code> were seeing errors. (<a href="https://github.com/simonw/datasette/issues/2691">#2691</a>)</li>
<li>The <a href="https://docs.datasette.io/en/latest/internals.html#database-close">database.close()</a> method now also shuts down the write connection for that database.</li>
<li>New <a href="https://docs.datasette.io/en/latest/internals.html#datasette-close">datasette.close()</a> method for closing down all databases and resources associated with a Datasette instance. This is called automatically when the server shuts down. (<a href="https://github.com/simonw/datasette/pull/2693">#2693</a>)</li>
<li>Datasette now includes a pytest plugin which automatically calls <code>datasette.close()</code> on temporary instances created in function-scoped fixtures and during tests. See <a href="https://docs.datasette.io/en/latest/testing_plugins.html#testing-plugins-autoclose">Automatic cleanup of Datasette instances</a> for details. This helps avoid running out of file descriptors in plugin test suites that were written before the <code>Database(is_temp_disk=True)</code> feature introduced in Datasette 1.0a27. (<a href="https://github.com/simonw/datasette/issues/2692">#2692</a>)</li>
</ul>
</blockquote>
<p>Most of the changes in this release were implemented using Claude Code and the newly released Claude Opus 4.7.</p>
    
        <p>Tags: <a href="https://simonwillison.net/tags/datasette">datasette</a></p>

</details>