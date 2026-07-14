---
id: inbox_edfed425
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/14/uvx-github-actions-cache/#atom-everything"
author: ""
published_at: 2026-07-14T00:56:20+00:00
fetched_at: 2026-07-14T01:15:50.483033+00:00
content_hash: "a07fd80e8f2f9cf433db0b300554d852bc7e5405ecd9abc7e4c243c4e3fbb241"
lang: en
caption_quality: None
raw: true
topics: []
---

# Using uvx in GitHub Actions in a cache-friendly way

TIL: Using uvx in GitHub Actions in a cache-friendly way 
 I finally found a cache-friendly recipe for using uvx tool-name in GitHub Actions workflows that I like. 
 The trick is setting a UV_EXCLUDE_NEWER: "2026-07-12" environment variable at the start of the workflow and then using that as part of the GitHub Actions cache key. This means any uvx tool-name commands will resolve to the most recent version as-of that date, and you can bust the cache and upgrade the tools by bumping the date in the future. 
 My goal here is to use Python tools in GitHub Actions without every run of the workflow hitting PyPI to download a fresh copy of the tool and its dependencies. 
 
 
 Tags: packaging , pypi , python , github-actions , uv