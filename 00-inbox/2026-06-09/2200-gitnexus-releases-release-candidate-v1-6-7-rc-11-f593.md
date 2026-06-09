---
id: inbox_aa5301f1
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.11"
author: "github-actions[bot]"
published_at: 2026-06-09T19:09:56+00:00
fetched_at: 2026-06-09T22:00:22.510740+00:00
content_hash: "f593f50bab775278face432e842b47ce20883e5d4d007a4e13b1ca62491240fb"
lang: en
caption_quality: None
raw: true
topics: []
---

# Release Candidate v1.6.7-rc.11

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.7-rc.11 \n Target base: 1.6.7 (rc #11 )\n Source commit (main): bd90d5b \n Release commit (versioned tree): 66b235f \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 chore: Sync Claude plugin manifests with the 1.6.6 release by @Copilot in #2090 
 feat(ingestion): M0 — taint/PDG substrate (schema + seams + spikes) ( #2080 ) by @magyargergo in #2092 
 fix(ingestion): lazy-load optional grammars so analyze never crashes when one is missing ( #2091 , #2093 ) by @magyargergo in #2101 
 feat(cpp): resolve inheritance-lattice member lookup by @azizur100389 in #2077 
 fix: batch query enrichment, bake FTS extension into CLI image, add FTS memory repro by @magyargergo in #2108 
 fix(install): graceful Kotlin optional-grammar install + accurate toolchain docs by @magyargergo in #2110 
 feat(cli): add gitnexus uninstall to reverse setup ( #2060 ) by @NilotpalK in #2062 
 feat(install): toolchain-free tree-sitter via vendored prebuilds by @magyargergo in #2113 
 fix(ci): drop broken -t 22 from prebuildify in build-tree-sitter-prebuilds by @magyargergo in #2121 
 fix(ci): green the tree-sitter prebuild matrix (npm-bundled prebuilds + arm64 runtime) by @magyargergo in #2122 
 
 Full Changelog : v1.6.6...v1.6.7-rc.11