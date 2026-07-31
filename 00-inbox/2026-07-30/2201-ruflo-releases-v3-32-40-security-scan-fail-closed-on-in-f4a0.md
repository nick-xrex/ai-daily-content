---
id: inbox_113536f4
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.40"
author: "ruvnet"
published_at: 2026-07-30T13:46:05+00:00
fetched_at: 2026-07-30T22:01:25.233686+00:00
content_hash: "f4a030b66111fda35fa774847f8a583967a7535511f23480641a00b8a5a21238"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.40 — security scan fail-closed on invalid --depth/--type/--target

Fixed 
 Security (reported privately via SECURITY.md, external reproduction + patch): ruflo security scan validated none of its --depth , --type , or --target flags. An unrecognised value did not error — it silently reduced or eliminated the scan while still printing "No security issues found!" and exiting 0. On a fixture whose only HIGH finding sat below the shallow-traversal budget, --depth full → --depth full (the CLI's own emitted value) silently flipped the critical/high exit-code gate from 1 to 0, and a typo'd --target produced a persisted CLEAN report that downstream status checks trusted as genuine. 
 All three flags now fail closed before anything is scanned or written: 
 
 --depth / --type validated against exhaustive Record&lt;ScanDepth, number&gt; maps with real type predicates (no unsafe casts that could silently re-disable the recursion limiter) 
 --depth full (never a real value, but emitted by the CLI's own statusline/announcements/generated CLAUDE.md/shipped agents) is deprecated-but-accepted → deep , with a warning, rather than breaking every caller told to use it 
 --type container (advertised but never implemented) now hard-rejects instead of silently reporting clean — breaking for any pipeline passing it, previously exited 0 
 --target validated for existence and directory-ness 
 
 246 lines of new tests cover depth-budget boundaries by nesting level, case sensitivity, a path-traversal-via- --type attempt, stdout/stderr separation, and no-persisted-report-on-rejection. 
 PR: #2866 
 Packages 
 `@claude-flow/cli`, `claude-flow`, and `ruflo` are all at 3.32.40 ; `latest`, `alpha`, and `v3alpha` dist-tags all point to it.