---
id: inbox_1f6ca419
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jun/16/datasette-tailscale/#atom-everything"
author: ""
published_at: 2026-06-16T16:18:20+00:00
fetched_at: 2026-06-17T22:00:31.126450+00:00
content_hash: "808b99953489040cfa53be1ff61567a8243f0f8956146a062415f135c685caaa"
lang: en
caption_quality: None
raw: true
topics: []
---

# datasette-tailscale 0.1a0

Release: datasette-tailscale 0.1a0 
 A very experimental alpha plugin which lets you do this: 
 datasette tailscale mydata.db \
 --ts-authkey tskey-auth-xxxx --ts-hostname datasette-preview
 
 This starts a localhost Datasette server with a Tailscale sidecar that connects it to your Tailnet, such that http://datasette-preview/ serves Datasette. 
 It's using the Python bindings for the experimental tailscale-rs library. I filed an issue asking if there's a cleaner way of setting up the proxy mechanism. 
 
 
 Tags: datasette , tailscale