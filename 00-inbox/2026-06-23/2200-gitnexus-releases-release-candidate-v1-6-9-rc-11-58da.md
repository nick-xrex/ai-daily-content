---
id: inbox_6e926da5
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.9-rc.11"
author: "github-actions[bot]"
published_at: 2026-06-23T11:31:50+00:00
fetched_at: 2026-06-23T22:00:22.283364+00:00
content_hash: "58daad78be852f24b403568374751a5d2bd7ea27406b2ec248754642398b4024"
lang: en
caption_quality: None
raw: true
topics: []
---

# Release Candidate v1.6.9-rc.11

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.9-rc.11 \n Target base: 1.6.9 (rc #11 )\n Source commit (main): 49ffd8e \n Release commit (versioned tree): 3a72964 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(taint): add Python source/sink model by @azizur100389 in #2253 
 fix(lbug): stop --pdg analyze double-free (skip LadybugDB close-destructor crash) + harden connection serialization by @magyargergo in #2264 
 feat(group): Kotlin Spring HTTP consumer extraction + provider parity with Java by @glier in #2254 
 feat(group): Support Django route extraction for multi-repo by @HuyNguyenDinh in #1836 
 feat(group): expand Java and Kotlin HTTP consumer extraction (re #1888 ) by @magyargergo in #2268 
 feat(taint): add conservative Java source/sink model by @azizur100389 in #2267 
 perf(group/http): skip source parse for graph-covered route files ( #2138 Part 2) by @henry201605 in #2265 
 feat(group): cross-repo call trace using PDG by @magyargergo in #2269 
 fix(lang-kotlin): support fun interface extraction via tree-sitter-kotlin re-vendor by @glier in #2271 
 feat(group): resolve cross-file named HTTP handlers ( #2275 ) by @magyargergo in #2277 
 
 New Contributors 
 
 @HuyNguyenDinh made their first contribution in #1836 
 
 Full Changelog : v1.6.8...v1.6.9-rc.11