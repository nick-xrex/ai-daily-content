---
id: inbox_57fab72e
date: 2026-05-21
source_ref: "[[00-inbox/2026-05-21/1800-ruflo-releases-v3-7-0-alpha-76-adr-127-adr-128-github-s-4594]]"
title: "v3.7.0-alpha.76 — ADR-127 + ADR-128 (.github stack + init bundle reduce) + 5 fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.76
source: ruflo-releases
published_at: 2026-05-21T20:36:23+00:00
fetched_at: 2026-05-22T18:08:46.125589+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.7.0-alpha.76（alpha.72→alpha.76，May 20-21）完成 ADR-127/128 執行，重點瘦身和安全強化。ADR-128 init bundle reduce：agents 98→17（domain-specific 需明確 --all-agents）、commands 176→16（9 orphan 刪除、78 ambiguous 升級一級），skill source-of-truth 修復優先載入 npm package 內 .claude/skills/ 避免舊狀態。ADR-127 強化 .github stack：github-safe.js v1.0.0 含 256KB body cap、smoke tests 驗證 injection 安全、action SHA pinning、deprecated actions 掃描（actions/checkout@v3→@v4）。新增 5 個 CI smoke jobs（supply chain 驗證）。Upstream ruvnet/neural-trader 同步至 v2.9.0。"
key_points:
  - "Init bundle 激進瘦身：agents 98→17、commands 176→16 大幅降低新用戶認知負載和 onboarding 摩擦"
  - "5 個 supply-chain smoke tests（injection/pin/deprecated actions/attribution/WASM init）提升 CI 穩健性"
  - "Skill source-of-truth 修復：優先載入 package bundled skills 避免舊狀態，解決 fresh install 陷阱"
tags: [init-bundle-optimization, supply-chain-hardening, ci-automation, adr-driven, bundle-reduction]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.7.0-alpha.76 — ADR-127 + ADR-128 (.github stack + init bundle reduce) + 5 fixes

Ruflo v3.7.0-alpha.76（alpha.72→alpha.76，May 20-21）完成 ADR-127/128 執行，重點瘦身和安全強化。ADR-128 init bundle reduce：agents 98→17（domain-specific 需明確 --all-agents）、commands 176→16（9 orphan 刪除、78 ambiguous 升級一級），skill source-of-truth 修復優先載入 npm package 內 .claude/skills/ 避免舊狀態。ADR-127 強化 .github stack：github-safe.js v1.0.0 含 256KB body cap、smoke tests 驗證 injection 安全、action SHA pinning、deprecated actions 掃描（actions/checkout@v3→@v4）。新增 5 個 CI smoke jobs（supply chain 驗證）。Upstream ruvnet/neural-trader 同步至 v2.9.0。

### 重點
- Init bundle 激進瘦身：agents 98→17、commands 176→16 大幅降低新用戶認知負載和 onboarding 摩擦
- 5 個 supply-chain smoke tests（injection/pin/deprecated actions/attribution/WASM init）提升 CI 穩健性
- Skill source-of-truth 修復：優先載入 package bundled skills 避免舊狀態，解決 fresh install 陷阱

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.76)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Consolidated release covering 5 alpha bumps (alpha.72 → alpha.76, May 20–21, 2026). Three packages: @claude-flow/cli , claude-flow (umbrella), ruflo (wrapper). All on latest , alpha , v3alpha dist-tags. 
 Highlights 
 ADR-128 — Init bundle reduce + refactor (alpha.76) 
 
 Default agent count: 98 → 17. agents.all default flipped from true to false . Domain-specific subtrees ( flow-nexus/ , payments/ , data/ ) now opt-in via --all-agents or explicit --agent-category . 
 Default command count: 176 → 16. 9 truly-orphan flow-nexus/ commands deleted; 78 ambiguous ones promoted to first-class COMMANDS_MAP keys. 
 Skill source-of-truth fix. The cli npm package now ships 34 SKILL.md files inside .claude/skills/ . Previously, fresh users got whatever was in ~/.claude/skills/ from prior installs — a stale-state trap. findSourceDir 's existing guard at executor.ts:1974 now resolves to the package's bundled skills first. 
 9 forked agents removed from init template (let plugins own them). Largest divergence was memory-specialist.md at 1,049 diff lines vs the ruflo-rag-memory plugin copy. 
 New CI smoke smoke-init-bundle-invariants.mjs asserts no orphans, no plugin-init agent overlap, every skill dir has a SKILL.md . 
 
 PR #2096 (ADR), PR #2097 (impl), closes #2095 . 
 ADR-127 — .github stack modernization (alpha.74, alpha.75) 
 
 Static-contract smokes for the .github skills/agents/commands surface:
 
 smoke-github-safe-injection.mjs — 10 adversarial body cases through both github-safe.js copies (backticks, $() , semicolons, &gt;256KB, empty). Accepts both helper-side rejection and kernel-side E2BIG (Linux argv limit). 
 smoke-github-actions-pins.mjs — asserts every uses: is SHA-pinned or in .github/supply-chain/allowed-deps.json . 
 smoke-deprecated-actions.mjs — scans 5 trees; fails on actions/checkout@v3 , actions/setup-node@v3 , actions/create-release@* , actions/upload-release-asset@* . 
 smoke-attribution-opt-in.mjs — no hardcoded attribution strings; opt-in template variables only. 
 
 
 github-safe.js v1.0.0 — exposes GITHUB_SAFE_VERSION , enforces 256 KB body cap. 
 swarm-pr.md + swarm-issue.md injection fix — ${{ github.event.comment.body }} now goes through mktemp temp-file indirection (both dogfood and init-template copies). 
 All actions/checkout@v3 → @v4 across 5 skills + 13 agents + 19 commands + 5 init-template agents that the initial sed missed (post-publish follow-up in alpha.75). 
 .github/supply-chain/allowed-deps.json gains an actions block alongside the existing 5-layer npm audit. 
 
 PR #2090 (ADR), PR #2094 (impl), b4e177667 (alpha.75 follow-up), closes #2089 . 
 ADR-126 — Neural-trader substrate integration (alpha.71 in the prior release; substrate is still alpha.76) 
 Bench/perf/security suite shipped as PR #2081 : 4 new benchmarks under plugins/ruflo-neural-trader/benchmarks/ (signal-generation, backtest-throughput, memory-recall, portfolio-cg), an 18% Neumann perf gain in sublinear-adapter.mjs via ping-pong Float64Array buffers, and a 3-layer supply-chain + static-secret audit. 
 Bug fixes 
 
 
 
 Issue / PR 
 Fix 
 
 
 
 
 #2073 (memory export returned null values) 
 listEntries and bridgeListEntries gain an includeContent flag; memory_export MCP tool now passes it. Also adds memory retrieve --value-only for pipe-friendly extraction. 
 
 
 #2078 (Co-Authored-By trailer added ruv@ruv.net to user repos) 
 settings-generator.ts now uses ruflo-bot &lt;ruflo-bot@users.noreply.github.com&gt; for opt-in attribution. 
 
 
 #2080 / Task #55 (native sublinear CG dispatch) 
 sublinear-adapter.ts detects MCP-tool availability via globalThis probe + RUFLO_SUBLINEAR_NATIVE env var. 40-60× when native is present. 
 
 
 #2086 (ruvllm WASM bootstrap not exposed via MCP) 
 loadRuvllmWasm() now awaits mod.initRuvllmWasm() . ruvllm_status deliberately uses a separate un-init loader so it stays a pure diagnostic. New CI smoke smoke-ruvllm-wasm-auto-init.mjs guards 12 invariants. Closes #2086 . 
 
 
 
 CI / supply chain additions 
 5 new smoke jobs gating future regressions, all path-filtered: 
 
 ruvllm-wasm-auto-init-smoke ( #2086 ) 
 github-safe-injection-smoke ( #2089 ) 
 github-actions-pins-smoke ( #2089 ) 
 deprecated-actions-smoke ( #2089 ) 
 init-bundle-invariants-smoke ( #2095 ) 
 
 Plus tighter scan coverage in smoke-deprecated-actions.mjs (5 trees instead of 3, catches both dogfood and init-template subtrees). 
 Upstream coordination 
 ruvnet/neural-trader PRs #132 – #138 all merged + workflow fix (PR #139 ) to replace deprecated actions/{create-release,upload-release-asset}@v1 with native gh release create / gh release upload . Tagged v2.9.0 there (CI publish gated on Actions budget). 
 Try it 
 npx ruflo@latest init
 # default install now ships 17 agents + 16 commands + 30 skills + helpers 
 # (vs the 98/176/0 of alpha.71) 
 Or upgrade in place: 
 npm i -g ruflo@latest # 3.7.0-alpha.76 
npm i -g @claude-flow/cli@latest 
 Out of scope, flagged for follow-up 
 
 General plugin-vs-plugin collision when two plugins both ship agents/coder.md . ADR-128 Phase 2 shrank the init-template-vs-plugin surface but didn't solve the plugin-vs-plugin case. Needs its own ticket. 
 pull_request_target + secrets.* TOCTOU scan (Layer 6 in supply-chain audit). Informational-only, no hard-fail precedent yet. 
 Dependabot / Renovate for uses: refs. Net-new automation pattern, would need its own ADR. 
 
 Closed in this release 
 #2073 , #2078 , #2086 , #2089 , #2095 . PRs: #2077 , #2079 , #2080 , #2081 , #2088 , #2090 , #2094 , #2096 , #2097 , #2079 . 
 🤖 Generated with RuFlo

</details>