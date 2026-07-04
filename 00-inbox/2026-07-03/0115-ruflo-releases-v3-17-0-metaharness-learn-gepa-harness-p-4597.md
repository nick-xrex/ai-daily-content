---
id: inbox_693ec14b
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.17.0"
author: "ruvnet"
published_at: 2026-07-03T18:24:16+00:00
fetched_at: 2026-07-04T01:15:53.897516+00:00
content_hash: "4597d6ca35884a411a19d68e0d98e4139fc654bbd34b845a4f856328b9639ed4"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.17.0 — MetaHarness learn + GEPA: harness policies become measured, evolved artifacts

v3.17.0 — MetaHarness learn + GEPA: harness policies become measured, evolved artifacts 
 This release closes the harness-policy lifecycle loop: learn a policy from a scored task corpus → audit what it compiles to → evolve it against fixed benchmarks → analyze why runs fail. Two new MCP tools (13 → 15), two new CLI subcommands (11 → 13), two new skills, and version-pin upgrades across the @metaharness/* family. 
 New: metaharness learn — learned policies instead of hand-tuned prompts 
 Wraps upstream metaharness@0.3.0 's ADR-235 GEPA learning harness. Instead of a human editing a system prompt and eyeballing the result, learn mutates the harness genome, scores candidates against held-out SWE-bench-style slices, and only promotes measured winners. 
 # $0 dry-run — resolves the slice and prices the run, no model calls 
npx ruflo metaharness learn --host claude-code --model haiku --slice slices/lite.json

 # real run — explicit spend opt-in at every layer 
npx ruflo metaharness learn --repo ~ /src/metaharness --host claude-code \
 --model haiku --slice slices/lite.json --run --timeout-ms 1800000 
 
 $0 by default — spending requires --run (CLI) / run: true (MCP tool metaharness_learn ) 
 Needs a metaharness repo checkout ( --repo or $METAHARNESS_REPO ); without one you get a structured {status: "checkout-required"} payload with clone instructions — a precondition report, not an error 
 
 New: metaharness gepa — genome inspection and auditing 
 Surfaces the @metaharness/darwin@0.8.0 GEPA library entry ( @metaharness/darwin/gepa ) — the first plugin surface with no CLI binary behind it. 
 npx ruflo metaharness gepa --op genome # load + validate the shipped cand-6 genome 
npx ruflo metaharness gepa --op render # genome → the system prompt it compiles to 
npx ruflo metaharness gepa --op validate --path my-genome.json --alert-on-invalid # CI gate 
npx ruflo metaharness gepa --op analyze --transcript run.json # failure-class breakdown 
 Why it matters: evolved policies ship as genome JSON, but the behavior lives in the system prompt the genome compiles to. --op render is the "what does this policy actually say?" view you want before adopting one. The shipped cand-6 genome is the first holdout-confirmed promotion (holdout gold 2/12 → 3/12, zero regressions, empty-patch rate 0.583 → 0.333). 
 Deliberately not surfaced: gepaOptimize — it takes an in-process bring-your-own-evaluator callback that can't cross a subprocess boundary. Import @metaharness/darwin/gepa directly, or use metaharness_evolve for sandbox-scored evolution. 
 Version pins refreshed 
 
 
 
 Package 
 Before 
 After 
 
 
 
 
 @metaharness/darwin 
 ~0.3.1 
 ~0.8.0 (GEPA engine, new evolve selection modes: pareto , clade , niche-steering , quality-diversity , behavioral-diversity , plus --crossover / --epistasis / --curriculum / --mutator ruvllm ) 
 
 
 metaharness 
 ~0.2.6 
 ~0.2.8 (learn arrives via @latest → 0.3.0) 
 
 
 @metaharness/redblue 
 ~0.1.1 
 ~0.1.4 
 
 
 @metaharness/kernel 
 ~0.1.0 
 ~0.1.2 
 
 
 
 Fixes 
 
 redblue stale-cache trap : the install cache dir is now versioned by the pin ( ~/.ruflo/redblue-cache-0.1.4 ), so pin bumps invalidate stale installs — previously a machine that cached 0.1.1 would serve it forever 
 gepa stale-install fallback : a pre-0.8.0 darwin in an ancestor node_modules throws ERR_PACKAGE_PATH_NOT_EXPORTED (no ./gepa subpath); gepa.mjs treats that as recoverable and falls back to its versioned cache 
 
 Validation 
 
 tsc clean build 
 MCP runtime contract: 171/171 assertions across all 15 tools 
 Plugin smoke suite: 120/120 steps 
 darwin 0.8.0 evolve / bench create|verify / security bench proven through the wrappers; redblue 0.1.4 attack preview proven via the new cache path 
 
 All ADR-150 constraints hold: @metaharness/* stays in optionalDependencies , every path degrades gracefully, ruflo remains fully operational with MetaHarness absent. 
 
 Deep-dive : full capabilities walkthrough (usage + rationale) → https://gist.github.com/ruvnet/cdc1bc2259cde127a418f861c3907e1e 
 PR : #2540