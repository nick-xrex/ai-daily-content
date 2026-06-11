---
id: inbox_925768f5
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.8-rc.9"
author: "github-actions[bot]"
published_at: 2026-06-10T13:02:10+00:00
fetched_at: 2026-06-10T22:04:18.434695+00:00
content_hash: "74e1b7453b89778b5831a826159c53f3ee8c53ba5c8c517152d15dacea2c0699"
lang: en
caption_quality: None
raw: true
topics: []
---

# Release Candidate v1.6.8-rc.9

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.8-rc.9 \n Target base: 1.6.8 (rc #9 )\n Source commit (main): 3d30b94 \n Release commit (versioned tree): 34c445f \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 fix(embeddings): create VECTOR index via conn.query, not the prepared path ( #2114 ) by @magyargergo in #2133 
 fix(docker): ship runtime-needed published assets (hooks/, skills/) into the image ( #2130 ) by @magyargergo in #2132 
 fix(hooks): silence MCP-owned-DB augment skip for strict hook runners ( #1913 ) by @magyargergo in #2134 
 feat(ingestion): Java Spring route annotation → Route node extraction by @henry201605 in #2078 
 feat: multi-branch indexing and branch-scoped querying ( #2106 ) by @magyargergo in #2137 
 fix: stop impact()/route_map under-reporting blast radius ( #2129 , #1858 , #1589 / #1852 ) by @magyargergo in #2136 
 fix(embeddings): resolve onnxruntime-common under pnpm-strict / pnpm dlx ( #307 ) by @magyargergo in #2139 
 fix(parse): survive non-cloneable worker results so large-repo analyze doesn't crash ( #2112 ) by @magyargergo in #2135 
 
 Full Changelog : v1.6.7...v1.6.8-rc.9