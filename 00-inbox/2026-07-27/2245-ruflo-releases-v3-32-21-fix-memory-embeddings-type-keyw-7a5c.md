---
id: inbox_cfc24661
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.21"
author: "ruvnet"
published_at: 2026-07-27T03:27:40+00:00
fetched_at: 2026-07-27T22:45:54.227227+00:00
content_hash: "7a5c49ca557ef82aba526dbca6ff610aa4747e59fadaddf0b7fdf7565a62c66d"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.21 — fix(memory/embeddings): --type keyword|hybrid + --threshold 0 (#2790)

Two-defect fix filed by markt-heximal in #2790 . 
 Fixed 
 --type keyword|hybrid silently ignored . memory search accepted, echoed, and then discarded the type flag — every search ran semantic. Now: 
 
 --type keyword — listEntries + substring match on key+content, key hit scores 1.0, content hit 0.7 
 --type hybrid — semantic ∪ keyword, dedup by (namespace, key), rerank 
 
 --threshold 0 silently replaced by fallback . Classic 0 || fallback idiom. Fixed with nullish coalescing at 3 reporter-flagged sites (memory.ts, embeddings.ts twice) plus 4 same-class hooks.ts sites (per reporter's "worth grepping more broadly" note). Also reconciled the memory.ts declared-default (0.7) vs code-fallback (0.3) disagreement. 
 Reporter's diagnostic invariant now holds: lower threshold returns ≥ results , not fewer. 
 Regression tests 
 4/4 E2E via real execFileSync against bin/cli.js: 
 
 --type keyword hits substring 
 --type keyword returns 0 for absent substring 
 --type hybrid ≥ semantic set 
 --threshold 0 ≥ --threshold 0.01 (monotonic) 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.21 
 Closes: #2790 .