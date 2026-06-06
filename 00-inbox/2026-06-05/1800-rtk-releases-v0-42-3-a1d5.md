---
id: inbox_6e3157e8
source: rtk-releases
source_type: rss
url: "https://github.com/rtk-ai/rtk/releases/tag/v0.42.3"
author: "rtk-release-bot[bot]"
published_at: 2026-06-05T16:29:54+00:00
fetched_at: 2026-06-05T18:00:31.970787+00:00
content_hash: "a1d5d00db83261f6741d859cbf9fe8e4b1e2a5fcb6bd6374d4aad70b11fae2e7"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.42.3

0.42.3 (2026-06-05) 
 Feats 
 
 feat(copilot): CLI native integration #2101 
 
 Fix 
 
 fix(docs): replace remaining MIT license references with Apache 2.0 #2084 
 fix: prevent crashes when output is piped #1048 close #1004 
 fix(grep): parse single-file output containing colons #1554 ; close #1436 . 
 fix(ls): preserve permission info as octal when -l/-la is passed #1675 
 fix(cicd): MIT to Apache 2.0 #2092 
 fix(pkg): rtk is Apache 2.0 and no MIT #2082 
 fix(hook): collapse bash line continuations before matching #1572 close Hook matcher: leading backslash-newline 
defeats command rewrite #1564 
 fix(gh,glab): don't pre-reject view/checks/run subcommands missing the id #2123 
 fix(git): fix panic on multibyte chars in commit output #1266 
 
 Other 
 
 docs(readme): add Portuguese translation #2128 
 doc(init): fix documentation inconsistencies arount rtk init #2173 
 fix(provider): sanatize more chars when encoding claude code project pathes #2172