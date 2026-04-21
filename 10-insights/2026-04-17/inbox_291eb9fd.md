---
id: inbox_291eb9fd
date: 2026-04-17
source_ref: "[[00-inbox/.../inbox_291eb9fd]]"
title: "datasette 1.0a28"
url: https://simonwillison.net/2026/Apr/17/datasette/#atom-everything
source: (resumed)
published_at: 2026-04-17T04:01:56+00:00
fetched_at: 2026-04-21T02:37:41.610462+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: ""
key_points:
tags: []
topics: []
importance: 1
novelty: 1
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 1.0a28



### 重點

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/17/datasette/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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
