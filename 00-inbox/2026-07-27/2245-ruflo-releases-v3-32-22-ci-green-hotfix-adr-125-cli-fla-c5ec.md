---
id: inbox_d7a3714d
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.22"
author: "ruvnet"
published_at: 2026-07-27T14:11:35+00:00
fetched_at: 2026-07-27T22:45:54.216743+00:00
content_hash: "c5ecbc4c9fa3d8c8a3f1e36e5c59bdca766acad5aa24e0365a25106b44f38fe3"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.22 — CI-green hotfix: ADR-125 CLI-flag precedence for RUFLO_MEMORY_SCAN_ON_WRITE (#2794)

Hotfix for the verification agent's #2794 finding — CI on main was red since 03:04 UTC because v3.32.17's #2752 MemPoison env var didn't match the ADR-125 §"CLI flag wins" pattern the audit script requires. 
 Fixed 
 Restructured the RUFLO_MEMORY_SCAN_ON_WRITE read so ctx.flags.scanContent takes precedence via nullish coalescing, with the exact ADR-125 comment format. Removed default: false from the --scan-content option so the parser leaves it undefined when unset (required for ?? env to see the env value). Explicit --no-scan-content still wins over the env var. 
 Verification 
 
 Audit script: ok: all CLAUDE_FLOW_ / RUFLO_ env var reads have documented CLI-flag precedence** 
 Regression tests still green: planflip-mempoison-2752 (6/6) + memory-search-2790 (4/4) 
 
 Closes: #2794 .