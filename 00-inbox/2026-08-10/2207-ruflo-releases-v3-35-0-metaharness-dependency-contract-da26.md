---
id: inbox_f1a77c09
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.35.0"
author: "ruvnet"
published_at: 2026-08-10T14:22:37+00:00
fetched_at: 2026-08-10T22:07:37.220216+00:00
content_hash: "da26fbd0b623338bd29f4c3c09a7300ee0c2eea0447aa2837d51e36c24765935"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.35.0 — MetaHarness dependency-contract repair + ADR-381 sequential-evidence governance

v3.35.0 — MetaHarness dependency-contract repair + ADR-381 sequential-evidence governance 
 What's in this release 
 
 #2956 — Fixes a dependency-contract bug where a clean ruflo install shipped with zero MetaHarness packages on disk (they were declared as optional peer dependencies, which npm never auto-installs). MetaHarness packages are now explicit optionalDependencies , tilde-pinned, with a mandatory clean-install CI gate. 
 #2956 — Adds strict, statistically-governed evidence requirements (ADR-381) to the self-optimizing flywheel's promotion gate, bounding the family-wise false-promotion probability at ≤5% across an adaptively-chosen candidate stream. 
 Follow-up fix on #2956 — Code review of the PR before merge found and fixed 3 confirmed concurrency/epoch-boundary bugs in the new sequential-evidence machinery that could silently violate that ≤5% guarantee under concurrent or decoupled evaluation/registration timing. See the companion write-up for the full story in plain language: 
👉 https://gist.github.com/ruvnet/0202e6a060b04b3a4f5d9bd18345169d 
 #2957 — Version bump housekeeping + a stale test assertion fix ( distill-oracle.test.ts — a version-pinned command no longer matched the test's un-pinned substring check). 
 
 Upgrade 
 npx ruflo@latest --version # 3.35.0 
npx @claude-flow/cli@latest doctor --component metaharness 
 No breaking changes — this is a backward-compatible minor release (new optional dependencies, new doctor checks, new CLI/MCP surface for flywheel evidence-reset ). 
 Verification 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) published at 3.35.0 with latest / alpha / v3alpha dist-tags aligned, verified via npm view &lt;pkg&gt; dist-tags --json and a live npx ruflo@latest --version smoke test. 
 🤖 Generated with RuFlo