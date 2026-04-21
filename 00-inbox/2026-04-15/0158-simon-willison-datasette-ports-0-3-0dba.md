---
id: inbox_2b18d2c7
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Apr/15/datasette-ports/#atom-everything"
author: ""
published_at: 2026-04-15T02:50:57+00:00
fetched_at: 2026-04-21T01:58:22.517763+00:00
content_hash: "0dba3826542adf04494feb95da4fec3a7f7c298bf6f8d14eb76ab78243b1de5c"
lang: en
caption_quality: None
raw: true
topics: []
---

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