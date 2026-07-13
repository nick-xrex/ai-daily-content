---
id: inbox_2a825f86
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Faccf61c672e38104b3e26611ec3ebe0511e58848"
author: "magyargergo"
published_at: 2026-07-11T07:33:50+00:00
fetched_at: 2026-07-11T22:41:12.801348+00:00
content_hash: "c688674b3cb82493ba48ece2a028dc26a49e6627941cdcfe1a4a5c76cdc70142"
lang: en
caption_quality: None
raw: true
topics: []
---

# rc/accf61c672e38104b3e26611ec3ebe0511e58848: fix(tree-sitter): recover declarations after embedded NUL bytes (#2430)

fix(tree-sitter): recover from embedded NUL bytes 
 
 Normalize embedded NUL bytes only in parser input so tree-sitter keeps recovering through the full source shape. Pass the file label through the worker for diagnostics and cover both direct-string and callback parse paths with regression tests. 
 
 
 fix(review): align safe-parser contract count 
 
 
 test(tree-sitter): cover worker NUL diagnostics ( #2430 )