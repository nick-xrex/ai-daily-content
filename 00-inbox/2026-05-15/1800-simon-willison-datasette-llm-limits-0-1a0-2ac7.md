---
id: inbox_80d9be79
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/May/15/datasette-llm-limits/#atom-everything"
author: ""
published_at: 2026-05-15T00:42:09+00:00
fetched_at: 2026-05-17T18:00:24.594082+00:00
content_hash: "2ac7c6c7f9cec159451d1f0b7def7d13895ad1765104adc705b586032ac05b75"
lang: en
caption_quality: None
raw: true
topics: []
---

# datasette-llm-limits 0.1a0

Release: datasette-llm-limits 0.1a0 
 This plugin works in conjunction with datasette-llm and datasette-llm-accountant to let you configure a per-user (or global) spending limit for LLM usage inside of Datasette. Configuration looks something like this: 
 plugins :
 datasette-llm-limits :
 limits :
 per-user-daily :
 scope : actor 
 window : rolling-24h 
 amount_usd : 1.00 
 
 
 
 Tags: llm , datasette