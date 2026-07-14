---
id: inbox_f732d404
date: 2026-07-13
source_ref: "[[00-inbox/2026-07-13/2231-ruflo-releases-v3-26-0-anv-phase-1-versioning-statuslin-817f]]"
title: "v3.26.0 — ANV Phase 1 versioning, statusline/funnel verification, CI + security fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.26.0
source: ruflo-releases
published_at: 2026-07-13T16:13:19+00:00
fetched_at: 2026-07-14T00:19:08.365906+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.26.0 推出 Agent-Native Versioning (ANV) Phase 1，版本號新增 `+ad.<n>.g<sha>.cat<generation>[.hal<tier>]` 後綴，透過新增 catalog-manifest.json 追蹤真實計數（164 個 agent 類型、387 個 MCP 工具、34 個 skills），而非虛報；`ruflo version --explain` 查詢，`ruflo version --require-catalog-gte N` 供腳本能力檢查。同步修復 7 項 CI 檢查失敗（npm override 衝突、env 變數漏列、輸出流程 bug）與安全問題（ReDoS 漏洞：正則表達式指數級回溯，36 重複 pattern 下耗時 2.8 秒；stderr 日誌加固；EOVERRIDE 衝突修復）。Statusline promo disclosure 寬限期從 72h 縮至 24h；驗證 funnel analytics 隱私合規（偽名 ID + 90 日輪換，無 hostname/email/path 外洩）。已發布 @claude-flow/cli@3.26.0、claude-flow@3.26.0、ruflo@3.26.0。"
key_points:
  - "ANV Phase 1：版本號帶上元數據及真實統計（164 agent types、387 MCP tools、34 skills），`--require-catalog-gte` 供能力檢查"
  - "修復 ReDoS 漏洞（正則指數級回溯 2.8 秒 @ 36 重複 pattern）與 stderr 日誌加固"
  - "Promo disclosure 72h→24h，funnel analytics 驗證隱私合規（無 hostname/email/path）"
tags: [ruflo, versioning, anv, security, mcp]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## v3.26.0 — ANV Phase 1 versioning, statusline/funnel verification, CI + security fixes

Ruflo v3.26.0 推出 Agent-Native Versioning (ANV) Phase 1，版本號新增 `+ad.<n>.g<sha>.cat<generation>[.hal<tier>]` 後綴，透過新增 catalog-manifest.json 追蹤真實計數（164 個 agent 類型、387 個 MCP 工具、34 個 skills），而非虛報；`ruflo version --explain` 查詢，`ruflo version --require-catalog-gte N` 供腳本能力檢查。同步修復 7 項 CI 檢查失敗（npm override 衝突、env 變數漏列、輸出流程 bug）與安全問題（ReDoS 漏洞：正則表達式指數級回溯，36 重複 pattern 下耗時 2.8 秒；stderr 日誌加固；EOVERRIDE 衝突修復）。Statusline promo disclosure 寬限期從 72h 縮至 24h；驗證 funnel analytics 隱私合規（偽名 ID + 90 日輪換，無 hostname/email/path 外洩）。已發布 @claude-flow/cli@3.26.0、claude-flow@3.26.0、ruflo@3.26.0。

### 重點
- ANV Phase 1：版本號帶上元數據及真實統計（164 agent types、387 MCP tools、34 skills），`--require-catalog-gte` 供能力檢查
- 修復 ReDoS 漏洞（正則指數級回溯 2.8 秒 @ 36 重複 pattern）與 stderr 日誌加固
- Promo disclosure 72h→24h，funnel analytics 驗證隱私合規（無 hostname/email/path）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.26.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights 
 
 Agent-Native Versioning (ANV) — Phase 1. ruflo version --explain now reports an advisory 
 +ad.&lt;n&gt;.g&lt;sha&gt;.cat&lt;generation&gt;[.hal&lt;tier&gt;] suffix alongside the normal semver, backed by a new 
 catalog-manifest.json with real, git-measured counts (currently 164 agent types, 387 MCP tools, 
34 skills) — never fabricated numbers, and no benchmark tier claimed without a real signed GAIA/HAL 
submission. Plain ruflo --version / -V and bare ruflo version are unaffected (still plain semver, 
npm-range-safe build metadata). ruflo version --require-catalog-gte N gives scripts a capability 
gate. See the ANV proposal . 
 Statusline promo disclosure grace period shortened from 72h to 24h. The disclosure/opt-out text 
(ending in · manage: ruflo settings , enforced at the content-validation layer) still shows for the 
full window before any promotional content is eligible — just a shorter window now. 
 Verified the funnel analytics pipeline: promo_impression / promo_open events are tracked with a 
pseudonymous, 90-day-rotating ID and daily-bucket timestamps only — no hostname, username, email, or 
path ever leaves the machine. Verified the sponsored-proxy feature remains a fully separate, 
never-bundled opt-in (per consent.ts 's "four+ distinct decisions, never bundled" design). 
 Confirmed the existing critical-helper auto-refresh mechanism ( autoRefreshHelpersIfStale ) correctly 
propagates the updated statusline.cjs to already-initialized projects on their next ruflo command 
— no re- init required. 
 
 Fixes 
 
 PR #2622 CI (7 failing checks) — an npm overrides /direct-install conflict in a CI smoke step, 8 
funnel/statusline env vars missing from the CLI-flag-precedence audit's escape-hatch list, a silently 
renamed regression-guard variable, a stdout/stderr contract bug in the shared CLI output formatter 
(warnings/info/debug/trace now correctly go to stderr, matching printError ), and a help-text 
ordering regression. 
 Security : fixed a confirmed exponential-backtracking ReDoS (measured: 2.8s at 36 pattern 
repetitions) in the shared npx-hook flag-list regex; stopped inheriting a subprocess's raw stderr in 
the helper/config signing scripts (clear-text-logging hardening); fixed an EOVERRIDE conflict where 
 @claude-flow/cli/package.json declared both overrides.agentdb and optionalDependencies.agentdb 
for the same package (now uses npm's canonical $agentdb self-reference). 
 
 Packages published 
 @claude-flow/cli@3.26.0 , claude-flow@3.26.0 , ruflo@3.26.0 — latest / alpha / v3alpha dist-tags 
all aligned.

</details>