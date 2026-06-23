---
id: inbox_9983f529
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.13.0"
author: "ruvnet"
published_at: 2026-06-22T14:43:45+00:00
fetched_at: 2026-06-22T22:03:43.592381+00:00
content_hash: "c2735b9a616cd1b04925051e69cc11201b5202659208ba5de4a50f7cbc0d0257"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.13.0 — Darwin Mode integration (@metaharness/darwin)

✨ Darwin Mode integration 
 Ships @metaharness/darwin@0.3.1 as ruflo's harness-evolution layer per ADR-153 . Also bumps the metaharness umbrella to ~0.2.6 to pick up new subcommands ( harness validate , compare , score , genome , threat-model , oia-manifest , analyze-repo , --wizard , --with-wasm ). 
 
 The model is frozen; the harness evolves. 
 
 What this lets you do 
 Mutate, score, promote — harness-evolve mutates one of seven policy surfaces (planner / contextBuilder / reviewer / retryPolicy / toolPolicy / memoryPolicy / scorePolicy), sandbox-scores each variant, and promotes only measured wins. The foundation model never changes; the operating system around it does. 
 # Dry-run plan (no --confirm yet) 
npx ruflo metaharness evolve --repo . 

 # Actually evolve (small shape — minutes) 
npx ruflo metaharness evolve --repo . --confirm --generations 3 --children 3

 # Quality-diversity sampling with crossover 
npx ruflo metaharness evolve --repo . --confirm --selection quality-diversity --crossover 
 Darwin Shield — harness-security-bench wraps the upstream's own ADR-155: evolves a champion security-detection harness against a 10-vuln / 9-decoy ground-truth corpus and grades it on TPR / FPR / patch-pass / repro / unsafe / cost vs four baselines. This is the closest reference implementation for ruflo's own ADR-155 nightly self-learning security harness (#2417) — running it periodically gives Loop A its empirical reward-signal floor. 
 # Quick smoke (1 cycle, default population) 
npx ruflo metaharness security-bench

 # Deeper run (CI gate: fail if any acceptance gate fails) 
npx ruflo metaharness security-bench --population 4 --cycles 3 --alert-on-fail 
 Bench suites — harness-bench creates and verifies fixed-corpus evaluation suites for evolve --bench . Decouples scoring from npm test . 
 npx ruflo metaharness bench --op create --repo . --out /tmp/suite.json
npx ruflo metaharness bench --op verify --suite /tmp/suite.json 
 MCP tools (3 new) 
 All three are also callable from any Claude Code agent: 
 
 metaharness_evolve — full param surface (generations / children / concurrency / sandbox / selection / crossover / epistasis / curriculum / risk-budget / fdr / tie / bench / mutator / ruvllm-url / confirm / alert-on-no-improvement) 
 metaharness_security_bench — population / cycles / seed / alert-on-fail 
 metaharness_bench — op / repo / suite / out 
 
 Safety 
 
 evolve requires --confirm ; without it, returns a dry-run plan (defense in depth over the upstream safety.ts layer) 
 Ruflo caps: --generations 1..50 , --children 1..20 , --concurrency 1..8 , --population 1..20 , --cycles 1..100 
 Upstream exit code 99 ("safety-disqualified") propagates verbatim — not remapped — so CI can distinguish evolution failure from a variant tripping the safety inspection layer 
 All three scripts emit {degraded: true, reason: 'metaharness-darwin-not-available'} and exit 0 when the optional dep is absent 
 
 Architectural compliance 
 All four ADR-150 constraints honored: 
 
 
 
 # 
 Constraint 
 How 
 
 
 
 
 1 
 Removable 
 npm ls --without @metaharness/* still produces a working CLI 
 
 
 2 
 Optional in package.json 
 Added to optionalDependencies only, never dependencies 
 
 
 3 
 Graceful degradation 
 _darwin.mjs catches MODULE_NOT_FOUND / 404 / network errors; emits structured degraded payload; exits 0 
 
 
 4 
 CI-absent-path coverage 
 test-graceful-degradation.mjs extended; 16/16 assertions pass (8 skills × 2 contracts) 
 
 
 
 Distribution 
 
 
 
 Package 
 latest 
 alpha 
 v3alpha 
 
 
 
 
 @claude-flow/cli 
 3.13.0 
 3.13.0 
 3.13.0 
 
 
 claude-flow 
 3.13.0 
 3.13.0 
 3.13.0 
 
 
 ruflo 
 3.13.0 
 3.13.0 
 3.13.0 
 
 
 
 How to try it 
 # Pulls 3.13.0 + @metaharness/darwin 
npx ruflo@latest metaharness evolve --repo /path/to/your/repo
npx ruflo@latest metaharness security-bench 
 Or in Claude Code, add the MCP server and use the new tools directly: 
 claude mcp add claude-flow -- npx -y @claude-flow/cli@latest
 # Then in Claude Code: call mcp__claude-flow__metaharness_evolve, etc. 
 Cross-references 
 
 🔗 ADR-153 (Darwin Mode integration): ruvnet/ruflo 
 🔗 Feature PR: #2440 (merged at a67e0ea ) 
 🔗 Release PR: #2441 (merged at 0b00665 ) 
 🔗 Companion ADR-155 (nightly self-learning security harness): #2417 + #2418 
 📦 Upstream Darwin: @metaharness/darwin@0.3.1 
 📦 Upstream umbrella: metaharness@0.2.6 
 
 
 🤖 Generated with RuFlo