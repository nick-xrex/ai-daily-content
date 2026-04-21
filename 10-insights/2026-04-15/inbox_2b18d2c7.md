---
id: inbox_2b18d2c7
date: 2026-04-15
source_ref: "[[00-inbox/.../inbox_2b18d2c7]]"
title: "datasette-ports 0.3"
url: https://simonwillison.net/2026/Apr/15/datasette-ports/#atom-everything
source: simon-willison
published_at: 2026-04-15T02:50:57+00:00
fetched_at: 2026-04-21T03:14:54.594161+00:00
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

## datasette-ports 0.3



### 重點

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/15/datasette-ports/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# datasette-ports 0.3

<p><strong>Release:</strong> <a href="https://github.com/datasette/datasette-ports/releases/tag/0.3">datasette-ports 0.3</a></p>
    <p>A small update for my tool for helping me figure out what all of the Datasette instances on my laptop are up to.</p>
<blockquote>
<ul>
<li>Show working directory derived from each PID</li>
<li>Show the full path to each database file</li>
</ul>
</blockquote>
<p>Output now looks like this:</p>
<pre><code>http://127.0.0.1:8007/ - v1.0a26
  Directory: /Users/simon/dev/blog
  Databases:
    simonwillisonblog: /Users/simon/dev/blog/simonwillisonblog.db
  Plugins:
    datasette-llm
    datasette-secrets
http://127.0.0.1:8001/ - v1.0a26
  Directory: /Users/simon/dev/creatures
  Databases:
    creatures: /tmp/creatures.db
</code></pre>
    
        <p>Tags: <a href="https://simonwillison.net/tags/datasette">datasette</a></p>

</details>