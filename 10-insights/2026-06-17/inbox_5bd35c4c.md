---
id: inbox_5bd35c4c
date: 2026-06-17
source_ref: "[[00-inbox/2026-06-17/2200-ruflo-releases-v3-12-2-kernel-panic-fix-cve-subcommand-2e5c]]"
title: "v3.12.2 — kernel-panic fix + cve subcommand fix + hooks hardening"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.12.2
source: ruflo-releases
published_at: 2026-06-17T22:45:40+00:00
fetched_at: 2026-06-18T22:06:56.778593+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.12.2 修復三大問題：(1) daemon 增殖導致 kernel panic（CRITICAL）——根因是 daemon 啟動的競態條件，使用 O_EXCL 原子 lockfile 修復，並移除 init.ts:424 的 shell `&`；race test 驗證 5 個並行 daemon 啟動現在僅存活 1 個倖存 daemon（修復前為 3–5+），曾實際事件累積 39 個殭屍 daemon 佔用 ~8.5 GiB 並誘發 macOS kernel panic；(2) security cve 命令從樁改為實作，委派 npm audit --json（同 GitHub Advisory DB 來源），新增 --check CVE-XXXX-NNNN 和 --severity {critical,high,medium,low} 篩選器，本倉庫驗證發現 37 個受影響套件；(3) .claude/helpers/* hooks 硬化（社區貢獻 @tjaiyen）——5 個實質 bug 修復，含真實超時機制（Promise.race 而非虛假「同步返回後計時器被清除」pattern）、signal 清理、截斷透明度、跨平台 slug 標準化，248 行增加 / 49 行移除跨 8 檔案。Dependabot bump 3/5 合併無衝突，@types/node、vitest、agent-browser 各版本精進。ruflo 三個包同步 3.12.2；無 API 破壞性變更，patch bump 符合 CLAUDE.md 發佈政策。"
key_points:
  - "Daemon 增殖 → kernel panic（CRITICAL）：O_EXCL 原子 lockfile + shell & 移除；race test 驗證 5 並行啟動 → 1 倖存（修復前 3–5+）；實例曾累積 39 zombie daemon 占 8.5 GiB 促發 macOS panic"
  - "CVE 檢查實裝：從樁改為 npm audit --json；支援 CVE-XXXX-NNNN 檢查及 severity filter；本倉庫驗證 37 受影響套件"
  - "Hooks 硬化 5 fixes：Promise.race 真實超時機制（非虛假同步返回模式）、signal cleanup、截斷透明度、跨平台 slug 標準化；248+/49− 跨 8 檔案"
tags: [daemon-lockfile-excl, kernel-panic-fix, npm-audit-cve, promise-race-timeout]
topics: [agents.mcp]
importance: 4
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.12.2 — kernel-panic fix + cve subcommand fix + hooks hardening

ruflo v3.12.2 修復三大問題：(1) daemon 增殖導致 kernel panic（CRITICAL）——根因是 daemon 啟動的競態條件，使用 O_EXCL 原子 lockfile 修復，並移除 init.ts:424 的 shell `&`；race test 驗證 5 個並行 daemon 啟動現在僅存活 1 個倖存 daemon（修復前為 3–5+），曾實際事件累積 39 個殭屍 daemon 佔用 ~8.5 GiB 並誘發 macOS kernel panic；(2) security cve 命令從樁改為實作，委派 npm audit --json（同 GitHub Advisory DB 來源），新增 --check CVE-XXXX-NNNN 和 --severity {critical,high,medium,low} 篩選器，本倉庫驗證發現 37 個受影響套件；(3) .claude/helpers/* hooks 硬化（社區貢獻 @tjaiyen）——5 個實質 bug 修復，含真實超時機制（Promise.race 而非虛假「同步返回後計時器被清除」pattern）、signal 清理、截斷透明度、跨平台 slug 標準化，248 行增加 / 49 行移除跨 8 檔案。Dependabot bump 3/5 合併無衝突，@types/node、vitest、agent-browser 各版本精進。ruflo 三個包同步 3.12.2；無 API 破壞性變更，patch bump 符合 CLAUDE.md 發佈政策。

### 重點
- Daemon 增殖 → kernel panic（CRITICAL）：O_EXCL 原子 lockfile + shell & 移除；race test 驗證 5 並行啟動 → 1 倖存（修復前 3–5+）；實例曾累積 39 zombie daemon 占 8.5 GiB 促發 macOS panic
- CVE 檢查實裝：從樁改為 npm audit --json；支援 CVE-XXXX-NNNN 檢查及 severity filter；本倉庫驗證 37 受影響套件
- Hooks 硬化 5 fixes：Promise.race 真實超時機制（非虛假同步返回模式）、signal cleanup、截斷透明度、跨平台 slug 標準化；248+/49− 跨 8 檔案

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.12.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Bundled fixes 
 #2407 — daemon proliferation → kernel panic (CRITICAL) 
 Atomic O_EXCL lockfile in daemon.ts + dropped the shell &amp; in init.ts:424 . Race test verified: 5 concurrent daemon start → 1 surviving daemon (was 3-5+). 
 One real incident accumulated 39 zombie daemons holding ~8.5 GiB and contributed to a macOS kernel panic on June 15. No longer possible. 
 #2403 — security cve no longer a stub 
 Now delegates to npm audit --json (same GitHub Advisory DB source as security scan ), extracts CVE IDs from via titles/URLs, supports --check CVE-XXXX-NNNN and --severity {critical,high,medium,low} filters. Local verify on this repo: 37 affected packages surfaced. 
 #2397 — .claude/helpers/* hooks hardening 
 Community contribution from @tjaiyen — 5 grounded bug fixes including real timeout via Promise.race (not the spurious "timer cleared on sync return" pattern), signal cleanup, truncation transparency, cross-platform slug normalization. 248+/49− across 8 files. 
 Dependabot bumps (3/5 merged cleanly) 
 
 @types/node 20.19.41 → 20.19.43 in /v3/@claude-flow/browser 
 vitest 4.1.6 → 4.1.9 in /v3/@claude-flow/browser + /plugins/ruflo-graph-intelligence 
 agent-browser 0.27.0 → 0.27.3 in /v3/@claude-flow/browser 
 
 ( #2384 + #2386 had merge conflicts; dependabot will rebase.) 
 Install 
 npx ruflo@3.12.2
 # or 
npm i ruflo@latest 
 Compatibility 
 All 3 packages × 3 dist-tags published in lockstep: 
 
 @claude-flow/cli@3.12.2 — latest, alpha, v3alpha 
 claude-flow@3.12.2 — latest, alpha, v3alpha 
 ruflo@3.12.2 — latest, alpha, v3alpha 
 
 No API breaking changes. Patch bump per CLAUDE.md publishing policy. 
 🤖 Generated with RuFlo

</details>