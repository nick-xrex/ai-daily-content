---
id: inbox_d80c97a4
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/12/sqlite-utils/#atom-everything"
author: ""
published_at: 2026-07-12T20:55:30+00:00
fetched_at: 2026-07-13T00:40:38.864049+00:00
content_hash: "4b5c0f32842e0a5c38da13f971a3eab238f7f14765f09dfddcedd58056b1e603"
lang: en
caption_quality: None
raw: true
topics: []
---

# sqlite-utils 4.1.1

Release: sqlite-utils 4.1.1 
 Mainly a fix for an edge case that regular Claude chat spotted while experimenting with the 4.1 release to answer a question about ON DELETE. 
 
 
 table.transform() now raises a TransactionError if called while a transaction is open with PRAGMA foreign_keys enabled and the table is referenced by foreign keys with destructive ON DELETE actions - CASCADE , SET NULL or SET DEFAULT . The pragma cannot be changed inside a transaction, so previously dropping the old table as part of the transform could fire those actions and silently delete or modify referencing rows. See Foreign keys and transactions for details and workarounds. ( #794 ) 
 The CLI and Python API documentation now cross-reference each other: CLI sections link to the equivalent Python API functionality and Python API sections link back to the corresponding CLI command. ( #791 ) 
 
 
 
 
 Tags: sqlite , sqlite-utils