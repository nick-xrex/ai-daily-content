---
id: inbox_8aa77b17
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jun/16/captcha-on-at-least-one-ampersand/#atom-everything"
author: ""
published_at: 2026-06-16T00:21:36+00:00
fetched_at: 2026-06-16T22:00:31.839277+00:00
content_hash: "f06a72e8654cd0a673155a44957da6b0c0423b9808c35714ebcf49bf5f9c1a6b"
lang: en
caption_quality: None
raw: true
topics: []
---

# Cloudflare CAPTCHA on at least one ampersand

TIL: Cloudflare CAPTCHA on at least one ampersand 
 I'm using Cloudflare's CAPTCHA (they call it a "Web Application Firewall &gt; Custom rules &gt; Managed Challenge" these days) to prevent crawlers from aggresively spidering my faceted search engine on this site, but I got fed up of even simple ?q=term searches triggering the challenge. 
 After some mucking around with Claude Code it turns out you can register the following rule instead, so the CAPTCHA only kicks in for search URLs containing at least one ampersand: 
 (http.request.uri.path wildcard r"/search/*" and http.request.uri.query contains "&amp;") 
 And now /search/?q=lemur works without triggering a CAPTCHA! 
 Also included: notes on trying out the Cloudflare MCP with Claude Code , though it turned out not to be able to edit the rules in question so I had Claude Code switch to the Cloudflare API instead. 
 
 
 Tags: captchas , cloudflare , model-context-protocol , claude-code