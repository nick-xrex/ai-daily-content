---
id: inbox_fdddc8d3
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/May/14/datasette-ip-rate-limit/#atom-everything"
author: ""
published_at: 2026-05-14T04:10:23+00:00
fetched_at: 2026-05-14T18:18:06.507640+00:00
content_hash: "063df6bbccac39c39a4e59c805bc56bb535675b871c81276ee45dbe5d56f6f85"
lang: en
caption_quality: None
raw: true
topics: []
---

# datasette-ip-rate-limit 0.1a0

Release: datasette-ip-rate-limit 0.1a0 
 The datasette.io site was being hammered by poorly-behaved crawlers, so I had Codex (GPT-5.5 xhigh) build a configurable rate limiting plugin to block IPs that were hammering specific areas of the site too quickly. 
 Here's the production configuration I'm using on that site for the new plugin: 
 datasette-ip-rate-limit :
 header : Fly-Client-IP 
 max_keys : 10000 
 exempt_paths :
 - " /static/* " 
 - " /-/turnstile* " 
 rules :
 - name : demo-databases 
 paths :
 - " /global-power-plants/* " 
 - " /legislators/* " 
 window_seconds : 60 
 max_requests : 60 
 block_seconds : 20 
 
 
 Tags: datasette , rate-limiting , codex