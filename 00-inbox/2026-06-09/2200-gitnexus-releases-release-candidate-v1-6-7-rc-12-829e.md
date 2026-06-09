---
id: inbox_b6946915
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.7-rc.12"
author: "github-actions[bot]"
published_at: 2026-06-09T19:47:41+00:00
fetched_at: 2026-06-09T22:00:22.507857+00:00
content_hash: "829eacdff8ecedc98621f2f1656a017d873fd859d85fec01769e6f2d6da76bd9"
lang: en
caption_quality: None
raw: true
topics: []
---

# Release Candidate v1.6.7-rc.12

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.7-rc.12 \n Target base: 1.6.7 (rc #12 )\n Source commit (main): 247ea43 \n Release commit (versioned tree): de545f4 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

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
 feat(mcp): paginate list_repos to avoid client token truncation ( #2119 ) by @magyargergo in #2120 
 fix(ci): make the prebuild PR push re-run-safe (--force-with-lease → --force) by @magyargergo in #2123 
 
 Full Changelog : v1.6.6...v1.6.7-rc.12