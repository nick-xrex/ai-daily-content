---
id: inbox_45e18091
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/May/4/tre-python-binding/#atom-everything"
author: ""
published_at: 2026-05-04T17:52:00+00:00
fetched_at: 2026-05-05T08:19:10.537284+00:00
content_hash: "20b1959eb31ebccc0540af0b54f35225829f16c2dd1602b872b7e3cfa63835e0"
lang: en
caption_quality: None
raw: true
topics: []
---

# TRE Python binding — ReDoS robustness demo

<p><strong>Research:</strong> <a href="https://github.com/simonw/research/tree/main/tre-python-binding#readme">TRE Python binding — ReDoS robustness demo</a></p>
        <p>If it's <a href="https://simonwillison.net/2026/May/4/redis-array/">good enough for antirez</a> to add to Redis I figured Ville Laurikari's <a href="https://github.com/laurikari/tre/">TRE</a> regular expression engine was worth exploring in a little more detail.</p>
<p>I had Claude Code build an experimental Python binding (it used <code>ctypes</code>) and try some malicious regular expression attacks against the library. TRE handles those much better than Python's standard library implementation, thanks mainly to the lack of support for backtracking.</p>
    
    
        <p>Tags: <a href="https://simonwillison.net/tags/security">security</a>, <a href="https://simonwillison.net/tags/python">python</a>, <a href="https://simonwillison.net/tags/regular-expressions">regular-expressions</a>, <a href="https://simonwillison.net/tags/c">c</a>, <a href="https://simonwillison.net/tags/ctypes">ctypes</a></p>