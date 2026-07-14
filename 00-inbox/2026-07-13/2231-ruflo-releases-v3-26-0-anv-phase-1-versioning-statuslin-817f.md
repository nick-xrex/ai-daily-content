---
id: inbox_f732d404
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.26.0"
author: "ruvnet"
published_at: 2026-07-13T16:13:19+00:00
fetched_at: 2026-07-13T22:31:53.200922+00:00
content_hash: "817fd1b4dc0425f155fd00bb68d6a780b6d8aee17342f1c65d235f7f74b8fb90"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.26.0 — ANV Phase 1 versioning, statusline/funnel verification, CI + security fixes

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