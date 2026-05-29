---
id: inbox_e1ab808c
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.4"
author: "ruvnet"
published_at: 2026-05-28T00:47:12+00:00
fetched_at: 2026-05-28T01:40:14.158106+00:00
content_hash: "5efae6f1c57f9ff34c6245775937658d2fc3b2d180fc50dc50e9c535f162c437"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.4 — statusline generator fix

Fixes #2195 : statusline generator delegates to hooks statusline --json instead of fragile local readers. ADR count now sums both v3/docs/adr/ and v3/implementation/adrs/ directories (128 total, not 87). New CI guard prevents regressions of this bug class. 
 Published to all three packages (@claude-flow/cli, claude-flow, ruflo) with latest/alpha/v3alpha dist-tags.