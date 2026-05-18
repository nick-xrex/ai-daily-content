---
id: inbox_69a528cc
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/May/12/datasette/#atom-everything"
author: ""
published_at: 2026-05-12T23:41:06+00:00
fetched_at: 2026-05-14T18:18:06.536803+00:00
content_hash: "ecfa700954032a9a937bef2c929c1142243d36ce3392b845acdc4543fc48cee5"
lang: en
caption_quality: None
raw: true
topics: []
---

# datasette 1.0a29

Release: datasette 1.0a29 
 
 
 New TokenRestrictions.abbreviated(datasette) utility method for creating "_r" dictionaries. #2695 
 Table headers and column options are now visible even if a table contains zero rows. #2701 
 Fixed bug with display of column actions dialog on Mobile Safari. #2708 
 Fixed bug where tests could crash with a segfault due to a race condition between Datasette.close() and Database.close() . #2709 
 
 
 That segfault bug was gnarly . I added a mechanism to Datasette recently that would automatically close connections at the end of each test, but it turned out that introduced a race condition where an in-flight query could sometimes be executing in a thread against a connection while it was being closed. I ended up solving that by having Codex CLI (with GPT-5.5 xhigh) create a minimal Dockerfile that recreated the bug. 
 
 
 Tags: projects , datasette