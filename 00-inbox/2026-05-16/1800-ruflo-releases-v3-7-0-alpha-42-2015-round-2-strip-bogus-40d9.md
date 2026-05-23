---
id: inbox_e3453a94
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.42"
author: "ruvnet"
published_at: 2026-05-16T13:02:27+00:00
fetched_at: 2026-05-22T18:00:34.016058+00:00
content_hash: "40d94353fe1238e9f7c285fac21910b0f05c251c9d9495512a7ad40c50dc8602"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.7.0-alpha.42 — #2015 round 2: strip bogus --kind flag

Hotfix on top of alpha.41 — the post-publish live regression check exposed a second-layer bug in the #2015 fix. 
 What round 1 missed 
 ruvector@0.2.25 rvf create accepts only: 
 
 -d, --dimension &lt;n&gt; (required) 
 -m, --metric &lt;metric&gt; (optional, default cosine) 
 
 Round 1 added the required --dimension 384 but left --kind browser-session in place. Commander's required-option check fires before its unknown-option check, so the original bug report ( #2015 ) only ever surfaced the dimension error — there was no way to discover the second layer without actually running the command end-to-end. 
 The live functional check after publishing alpha.41 surfaced it: 
 error: unknown option '--kind'
 
 What changed in alpha.42 
 
 Stripped --kind browser-session from all 5 call sites (TS source, compiled dist, replay-spike.sh , browser-agent.md , browser-record/SKILL.md ) + ADR prose example. 
 Tightened smoke-browser-rvf-create-flags.mjs to police BOTH invariants per line:
 
 --dimension / -d is present 
 --kind is absent 
 
 
 The smoke now uses an explicit PATHS_IN_SCOPE list (round 1's content-anchor was the very flag we just deleted). 
 
 Live functional check (everything green) 
 
 ruvector rvf create --dimension 384 (no --kind ): exit 0 , .rvf file written. 
 Published @claude-flow/cli@3.7.0-alpha.42 dist:113: --dimension present, --kind absent. 
 #2019 vectorBackend/graphAdapter functional test from alpha.41: still passes against @claude-flow/memory@3.0.0-alpha.16 . 
 verify.mjs precondition contract from #1880 : still holds (exit 2 for source-only, exit 1 for built tree with real regressions). 
 
 Packages 
 
 
 
 Package 
 Version 
 
 
 
 
 @claude-flow/cli 
 3.7.0-alpha.42 
 
 
 claude-flow 
 3.7.0-alpha.42 
 
 
 ruflo 
 3.7.0-alpha.42 
 
 
 @claude-flow/memory 
 3.0.0-alpha.16 (unchanged from alpha.41 release) 
 
 
 
 All latest / alpha / v3alpha dist-tags updated. 
 Commit: 905672021 
 🤖 Generated with RuFlo