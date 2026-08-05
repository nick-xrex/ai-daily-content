---
id: inbox_5e2cd400
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Aug/3/condense-json/#atom-everything"
author: ""
published_at: 2026-08-03T04:56:26+00:00
fetched_at: 2026-08-05T01:44:31.963368+00:00
content_hash: "12c674c41c83fb418fe4d8cffcb1b8ba3899f95efc7b1a37de64e3199d530e18"
lang: en
caption_quality: None
raw: true
topics: []
---

# condense-json 1.1

Release: condense-json 1.1 
 After shipping condense-json 1.0 I started integrating it into LLM, and found there were some desirable new features already: 
 
 
 Replacements object can now include values other than strings. These will be identified and used as structural replacements by condense_json() and uncondense_json() . #8 
 Objects can be used as the basis for merge operations. condense_json() will identify if there are objects that are a close match and will store instructions for keys to update or delete. uncondense_json() can then apply these merges. 
 
 
 I also added some round-trip tests using the Hypothesis property-based Python testing library. 
 
 
 Tags: json