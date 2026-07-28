---
id: inbox_58663a7f
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.19"
author: "ruvnet"
published_at: 2026-07-27T03:05:05+00:00
fetched_at: 2026-07-27T22:45:54.256584+00:00
content_hash: "934cfaf9bdd78a2b1f3050cf307238d7e7738b8052a0e9860c3d92edbf9e4f29"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.19 — OAS operator selector (#2763 dream-cycle)

Budget-aware consolidation-operator picker. Fourth of the four bounded dream-cycle items ready this session ( #2727 IB+VQ remains — real VQ codec, own PR). 
 Added 
 ruflo memory select-operator --budget N --entries K [--hint duplicates|verbose|patterns|general] 
 Rule-based picker over four consolidation operators: 
 
 
 
 Operator 
 Cost/entry 
 Max entries 
 Best when 
 
 
 
 
 merge 
 0.02 
 5000 
 Near-duplicate deterministic collapse 
 
 
 summarize 
 0.50 
 500 
 Verbose logs / traj steps sharing a theme 
 
 
 compress 
 1.50 
 200 
 High-fidelity pattern preservation 
 
 
 distill 
 3.00 
 100 
 Extract high-value patterns for ReasoningBank 
 
 
 
 Three selection rules: 
 
 Hint-driven pick when the hinted operator fits the budget. 
 Otherwise most-expensive-that-still-fits (spend the whole budget on best fidelity). 
 When nothing fits, fall back to merge with needsSplit + batch size ≤ budget/cost. 
 
 Advisory only in v1 — no automatic wire into memory consolidate (same safety pattern as #2760 SCM classifier). 
 Verification 
 
 Regression tests: 7/7 (all three rules + hint-fits, hint-doesnt-fit, ranking, needsSplit) 
 E2E matrix: 5 scenarios verified end-to-end (summarize-fits-exactly, distill-most-expensive-fit, tiny-budget-huge-set-merge-split, hint-ignored-when-doesnt-fit, distill-with-split) 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.19 
 Refs: dream-cycle #2763 (2026-07-23).