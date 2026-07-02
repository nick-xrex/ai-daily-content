---
id: inbox_cf85b39f
date: 2026-06-30
source_ref: "[[00-inbox/2026-06-30/2331-ruflo-releases-v3-16-2-adr-165-phase-1-5-critical-cves-90fe]]"
title: "v3.16.2 — ADR-165 Phase 1: 5 critical CVEs closed"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.16.2
source: ruflo-releases
published_at: 2026-06-30T02:44:36+00:00
fetched_at: 2026-07-02T00:15:15.476270+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.16.2 實踐 ADR-165 Phase 1，成功關閉 5 個重大 CVE（critical 0 → 0）。Root workspace 從 1 critical/6 high/31 moderate 降至 0 critical/0 high/31 moderate；v3 workspace 從 4 critical/33 high/57 moderate 降至 0 critical/27 high/58 moderate。具體修復的重大漏洞鏈：vitest GHSA-5xrq-8626-4rwp（CVSS 9.8 UI server 任意檔案讀寫+執行）、handlebars prototype-pollution RCE（工具鏈限定路徑驗證無用戶可達性）、protobufjs constructor-pollution。新增 CVE registry（16 current entries）與 CI gate（.github/workflows/cve-audit.yml，阻止 critical、警告 high）。113/113 PR 檢查通過、105/109 vitest 通過、npm audit --audit-level=critical exit 0。"
key_points:
  - "關閉 5 個 critical CVE：vitest (CVSS 9.8 UI server 任意檔案讀寫) 、handlebars 原型污染 RCE、protobufjs 構造器污染"
  - "新增 CVE CI gate（.github/workflows/cve-audit.yml）阻止 critical PR、警告 high 級、每日執行審計"
  - "v3 workspace 仍需 Phase 2 處理 27 個 high-severity 傳遞依賴鏈（3.17.0 目標）"
tags: [cve-remediation, security-audit, ci-gate, dependency-management, adr-165]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.16.2 — ADR-165 Phase 1: 5 critical CVEs closed

ruflo v3.16.2 實踐 ADR-165 Phase 1，成功關閉 5 個重大 CVE（critical 0 → 0）。Root workspace 從 1 critical/6 high/31 moderate 降至 0 critical/0 high/31 moderate；v3 workspace 從 4 critical/33 high/57 moderate 降至 0 critical/27 high/58 moderate。具體修復的重大漏洞鏈：vitest GHSA-5xrq-8626-4rwp（CVSS 9.8 UI server 任意檔案讀寫+執行）、handlebars prototype-pollution RCE（工具鏈限定路徑驗證無用戶可達性）、protobufjs constructor-pollution。新增 CVE registry（16 current entries）與 CI gate（.github/workflows/cve-audit.yml，阻止 critical、警告 high）。113/113 PR 檢查通過、105/109 vitest 通過、npm audit --audit-level=critical exit 0。

### 重點
- 關閉 5 個 critical CVE：vitest (CVSS 9.8 UI server 任意檔案讀寫) 、handlebars 原型污染 RCE、protobufjs 構造器污染
- 新增 CVE CI gate（.github/workflows/cve-audit.yml）阻止 critical PR、警告 high 級、每日執行審計
- v3 workspace 仍需 Phase 2 處理 27 個 high-severity 傳遞依賴鏈（3.17.0 目標）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.16.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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

</details>