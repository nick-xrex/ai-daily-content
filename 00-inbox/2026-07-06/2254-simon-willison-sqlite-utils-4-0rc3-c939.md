---
id: inbox_089c0610
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/6/sqlite-utils/#atom-everything"
author: ""
published_at: 2026-07-06T05:40:08+00:00
fetched_at: 2026-07-06T22:54:57.218134+00:00
content_hash: "c9390dd5e565d3a8307f717c3c640e5ce5c5b819a97499f8de3eb46438e43f6e"
lang: en
caption_quality: None
raw: true
topics: []
---

# sqlite-utils 4.0rc3

Release: sqlite-utils 4.0rc3 
 I hoped to release sqlite-utils 4.0 stable this weekend, but as I worked through the backlog of issues and PRs with a combination of Claude Fable 5 and GPT-5.5 the changelog since rc2 kept getting bigger . 
 The biggest new feature is support for introspecting and creating compound foreign keys - a feature that involves a subtle breaking change to table.foreign_keys and hence needed to land for the 4.0 stable release. 
 sqlite-utils also now follows SQLite's convention for case insensitive column names, which turned out to touch a bunch of different places at once . 
 
 
 Tags: projects , sqlite , sqlite-utils , annotated-release-notes , gpt , claude-mythos-fable