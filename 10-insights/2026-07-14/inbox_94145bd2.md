---
id: inbox_94145bd2
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-ruflo-releases-v3-30-0-spinner-verbs-default-on-startup-3a7b]]"
title: "v3.30.0 — spinner verbs (default ON) + startup announcements + rev-share scaffold"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.30.0
source: ruflo-releases
published_at: 2026-07-14T19:18:46+00:00
fetched_at: 2026-07-14T22:10:02.245124+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.30.0 引入三個新用戶接觸點（ADR-317, -318, -319）：1) Spinner verbs（預設開啟）— 37 個精選現在分詞混入 Claude Code spinnerVerbs，涵蓋記憶、優化、安全、代理類別（可設 RUFLO_NO_AUTO_ENABLE=1 停用）；2) Startup announcements（選擇加入）— 12 個精選條目在 Claude Code 啟動顯示（更高侵入性，需 RUFLO_AUTO_ENABLE_ANNOUNCEMENTS=1 啟用）；3) Developer revenue-share scaffold（Phase 0）— 50/50 Cognitum 贊助收益分享的客戶端骨架（後端 + Stripe Connect 為 Phase 1）。首次執行自動啟用機制透過 ~/.ruflo/first-run-enabled.json 標記（一次性），提供多個環境變數逃逸口。本版本亦修復並發會話 helper 覆蓋（.LOCKED 標記 + RUFLO_HELPERS_LOCKED=1）和 statusline URL 後綴遺失。"
key_points:
  - "37 個 spinner verbs 混入 ~/.claude/settings.json spinnerVerbs.verbs[]，升級自動啟用（預設），可透過環境變數或 `ruflo spinner disable` 停用"
  - "12 個 startup announcements 機制類似 spinner（選擇加入），需手動 enable 或 RUFLO_AUTO_ENABLE_ANNOUNCEMENTS=1"
  - "首次執行標記 (~/.ruflo/first-run-enabled.json) + 多重環境變數逃逸口（RUFLO_NO_AUTO_ENABLE、RUFLO_NO_AUTO_ENABLE_SPINNER），確保冪等性且跳過 CI/非 TTY"
tags: [ruflo, feature-release, ui, monetization, auto-enable]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.30.0 — spinner verbs (default ON) + startup announcements + rev-share scaffold

Ruflo v3.30.0 引入三個新用戶接觸點（ADR-317, -318, -319）：1) Spinner verbs（預設開啟）— 37 個精選現在分詞混入 Claude Code spinnerVerbs，涵蓋記憶、優化、安全、代理類別（可設 RUFLO_NO_AUTO_ENABLE=1 停用）；2) Startup announcements（選擇加入）— 12 個精選條目在 Claude Code 啟動顯示（更高侵入性，需 RUFLO_AUTO_ENABLE_ANNOUNCEMENTS=1 啟用）；3) Developer revenue-share scaffold（Phase 0）— 50/50 Cognitum 贊助收益分享的客戶端骨架（後端 + Stripe Connect 為 Phase 1）。首次執行自動啟用機制透過 ~/.ruflo/first-run-enabled.json 標記（一次性），提供多個環境變數逃逸口。本版本亦修復並發會話 helper 覆蓋（.LOCKED 標記 + RUFLO_HELPERS_LOCKED=1）和 statusline URL 後綴遺失。

### 重點
- 37 個 spinner verbs 混入 ~/.claude/settings.json spinnerVerbs.verbs[]，升級自動啟用（預設），可透過環境變數或 `ruflo spinner disable` 停用
- 12 個 startup announcements 機制類似 spinner（選擇加入），需手動 enable 或 RUFLO_AUTO_ENABLE_ANNOUNCEMENTS=1
- 首次執行標記 (~/.ruflo/first-run-enabled.json) + 多重環境變數逃逸口（RUFLO_NO_AUTO_ENABLE、RUFLO_NO_AUTO_ENABLE_SPINNER），確保冪等性且跳過 CI/非 TTY

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.30.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights — ADR-317, ADR-318, ADR-319 
 Three new placement surfaces for ruflo, sibling to the existing statusline promo row: 
 1. Spinner verbs ( ruflo spinner ... ) — DEFAULT ON 
 Ruflo appends its own curated "present-participle" verbs to Claude Code's spinnerVerbs.verbs[] in ~/.claude/settings.json , so the ✽ Channeling... rotation mixes ruflo verbs with Claude Code's built-ins. 37 verbs across memory, optimization, learning, security, agents, workflow + Cognitum-tagged categories. Default posture: ON for new installs and upgrades (opt-out via RUFLO_NO_AUTO_ENABLE=1 or ruflo spinner disable ). 
 Sample additions: Consulting the memory graph , Warming the HNSW index , Auditing for CVEs , Consulting Cognitum . 
 2. Startup announcements ( ruflo announcements ... ) — OPT-IN 
 Similar mechanism for Claude Code's companyAnnouncements — 12 curated entries shown at Claude Code startup, one per session. Higher intrusion profile than spinner (prominent line vs. per-spin flash), so opt-in via RUFLO_AUTO_ENABLE_ANNOUNCEMENTS=1 or ruflo announcements enable --yes . 
 3. Developer revenue-share ( ruflo funnel enroll/earnings/unenroll ) — Phase 0 scaffold 
 Client-side skeleton for the 50/50 Cognitum-sponsor rev-share. Response to "can we do something similar to kickbacks.ai?" — yes, and 60-70% of the plumbing (attribution, consent, rotation) already existed. This ships the CLI subcommands + consent domain + attribution token wiring. Backend enrollment + Stripe Connect are Phase 1 (blocks on legal). 
 First-run auto-enable mechanism ( session-restore hook) 
 Fires once per install (marker at ~/.ruflo/first-run-enabled.json ), then never again. Multiple env-var escape hatches: RUFLO_NO_AUTO_ENABLE , RUFLO_NO_AUTO_ENABLE_SPINNER , RUFLO_AUTO_ENABLE_ANNOUNCEMENTS . Skips in CI + non-TTY. Detached spawn — session-restore latency unchanged. One-line stderr notification names exactly what got enabled and how to disable. 
 Fixes bundled 
 
 Concurrent-session helper clobber (documented in CLAUDE.md): new .claude/helpers/.LOCKED marker + RUFLO_HELPERS_LOCKED=1 env opt-out. Users editing helpers directly can now protect their dev tree from being overwritten by sibling Claude Code sessions running stale cached @claude-flow/cli . 
 Statusline URL suffix correctly emits again (bug where concurrent-session corruption had wiped it earlier). 
 
 Upgrade notes 
 Every existing user upgrading past v3.29.x will see spinner verbs added to their ~/.claude/settings.json on their next Claude Code session (with backup + notification + one-command undo). Set RUFLO_NO_AUTO_ENABLE=1 before upgrading if you don't want this. 
 Related 
 
 PR #2676 — everything above 
 Tech-debt: #2679 — sync statusline-generator.ts with the committed helper's #2195 delegation build 
 Related issue: #2677 — @stuinfla 's excellent report on doctor --component memory being existence-only 
 
 Install 
 ```bash 
npx ruflo@latest init 
 or 
 npm install -g @claude-flow/cli@3.30.0 
```

</details>