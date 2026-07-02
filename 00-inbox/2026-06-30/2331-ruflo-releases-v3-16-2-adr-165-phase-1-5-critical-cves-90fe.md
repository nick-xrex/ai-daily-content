---
id: inbox_cf85b39f
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.16.2"
author: "ruvnet"
published_at: 2026-06-30T02:44:36+00:00
fetched_at: 2026-07-01T23:31:23.992760+00:00
content_hash: "90fe40a326ffd7519a368c7008a3219678f850ff1a88a1fd74abf0f7908efa16"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.16.2 — ADR-165 Phase 1: 5 critical CVEs closed

What's fixed in 3.16.2 
 PATCH release shipping ADR-165 Phase 1 — close every critical CVE in both workspaces. 
 Critical-severity advisories closed (5 → 0) 
 
 
 
 Workspace 
 Before 
 After 
 
 
 
 
 Root 
 1 critical, 6 high, 31 moderate (38 total) 
 0 critical , 0 high, 31 moderate (31 total) 
 
 
 v3 
 4 critical, 33 high, 57 moderate (97 total) 
 0 critical , 27 high, 58 moderate (88 total) 
 
 
 
 Each critical chain closed: 
 
 vitest — GHSA-5xrq-8626-4rwp (CVSS 9.8 — UI server arbitrary file read+exec) 
 handlebars — prototype-pollution RCE chain (toolchain-only path verified non-user-reachable) 
 protobufjs — constructor-pollution chain 
 Plus 2 additional v3 criticals via overrides 
 
 12 of 39 high-severity advisories also closed (the remaining 27 v3 highs need major-bump migrations — flagged for ADR-165 Phase 2). 
 Other deliverables in this release 
 
 CVE registry rewritten : 5 stale Jan-2026 entries → 16 current entries. CVE-REMEDIATION.ts::validateRemediation() now correctly returns allFixed: false with 1 known open (ADR165-OPEN-01 — PII pipeline wiring). 
 New CI gate : .github/workflows/cve-audit.yml blocks PRs on any critical, warn-only on high, runs on every PR + push + daily cron. 
 ADR-165 §9 evidence ledger updated with after-remediation npm audit metadata. 
 
 Verified 
 
 113/113 PR #2508 CI checks green 
 105/109 vitest pass (4 skip-conditional) 
 352/352 MCP tools pass ADR-112 audit 
 11/11 + 8/8 + 8/8 smoke contracts (business-pods, agentbbs, agenticow) 
 npm audit --audit-level=critical exit 0 in BOTH workspaces 
 
 Install / upgrade 
 npx ruflo@latest # 3.16.2 
npx @claude-flow/cli@latest # 3.16.2 
npx claude-flow@latest # 3.16.2 
 npm dist-tags 
 @claude-flow/cli latest=3.16.2 alpha=3.16.2 v3alpha=3.16.2
claude-flow latest=3.16.2 alpha=3.16.2 v3alpha=3.16.2
ruflo latest=3.16.2 alpha=3.16.2 v3alpha=3.16.2
 
 Related 
 
 ADR docs/adr/ADR-165-security-cve-posture-review.md 
 PR #2508 — fix(security): Phase 1 close-out 
 PR #2509 — chore(release): 3.16.1 → 3.16.2 
 
 Phase 2 (next release) 
 Targets 3.17.0 — automated cve-watch.yml + per-tool validator coverage audit + v3 high-severity transitive chain remediation.