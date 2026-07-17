---
id: inbox_19aff0dd
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/16/bad-codex-bug/#atom-everything"
author: ""
published_at: 2026-07-16T17:45:59+00:00
fetched_at: 2026-07-16T23:06:49.276994+00:00
content_hash: "a18088b01c4228dd8f9ef2d7207a6d0e4475fc4ae26fd4d95acb45c2c73a74b6"
lang: en
caption_quality: None
raw: true
topics: []
---

# Quoting Thibault Sottiaux

On file deletions. We’ve investigated a handful of reports where GPT-5.6 unexpectedly deleted files. 
 What we have found is that this most commonly occurs when: 
 
 Full access mode is enabled and codex is run without sandboxing protections, including without auto review being enabled 
 The model attempts to override the $HOME env var to define a temporary directory. 
 The model makes an honest mistake and mistakenly deletes $HOME instead. 
 
 &mdash; Thibault Sottiaux , describing a pretty gnarly Codex bug 

 Tags: codex , coding-agents , generative-ai , ai , llms