---
id: inbox_f8f4f4f1
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.36.0"
author: "ruvnet"
published_at: 2026-08-10T17:43:32+00:00
fetched_at: 2026-08-10T22:07:37.165630+00:00
content_hash: "d421b12f04563b9f0bb640b31a63ae175c6f734d70427c3cdefebf9d3cb46286"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.36.0 — @metaharness/turn-credit integration + stale pin fixes

v3.36.0 — @metaharness/turn-credit integration + stale pin fixes 
 What's in this release 
 
 metaharness#176 (upstream) shipped @metaharness/turn-credit (ADR-248 — recursive turn-level credit assignment for agent trajectories, based on AgentOPSD/arXiv:2608.05987), plus a bump to @metaharness/darwin 0.9.0 (ADR-249 additive scorer signal seams) and @metaharness/router 0.4.0 (new calibration-audit module). 
 This release brings ruflo's dependency contract in sync with that upstream work:
 
 Adds @metaharness/turn-credit@~0.1.0 as a new installable optionalDependency , following the same pattern as darwin/flywheel/radio (ADR-150) — dependency-free, ~65KB unpacked, no lifecycle scripts. 
 Fixes two stale pins the review turned up: @metaharness/darwin ( ~0.8.3 → ~0.9.0 ) and @metaharness/router 's peer range ( ^0.3.2 → ^0.4.0 ) — both had drifted out of range of what's actually published. 
 Bumps the no-cli-optdep-bloat-2561 CI guard's budget from 10 → 13, fixing a "zero slack" trap left by the previous release (v3.35.0) that would have broken on the very next unrelated optional dependency. 
 Fixes a live ReferenceError in a test file ( MH_DARWIN_PIN referenced but never imported) that had somehow slipped through v3.35.0's CI. 
 
 
 
 👉 Full plain-language write-up (what turn-credit does, why the pin bugs mattered, and a lesson learned about pnpm lockfile drift): https://gist.github.com/ruvnet/0202e6a060b04b3a4f5d9bd18345169d 
 Upgrade 
 npx ruflo@latest --version # 3.36.0 
npm install @metaharness/turn-credit # optional — new capability, not auto-installed by ruflo's own peer/opt-in design 
 No breaking changes — backward-compatible minor release. 
 Verification 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) published at 3.36.0 with latest / alpha / v3alpha dist-tags aligned, verified via npm view &lt;pkg&gt; dist-tags --json and a live npx ruflo@latest --version smoke test. 
 🤖 Generated with RuFlo