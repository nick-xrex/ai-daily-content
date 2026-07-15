---
id: inbox_782aa59e
source: gitnexus-releases
source_type: rss
url: "https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.20"
author: "github-actions[bot]"
published_at: 2026-07-14T02:23:03+00:00
fetched_at: 2026-07-14T22:00:21.506923+00:00
content_hash: "bf381429e2b45f5e439c1c0cdd9ab981889b57e5a9e81cfca2fe362eda63108e"
lang: en
caption_quality: None
raw: true
topics: []
---

# Release Candidate v1.6.10-rc.20

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.20 \n Target base: 1.6.10 (rc #20 )\n Source commit (main): f6c63f6 \n Release commit (versioned tree): 7de2b3f \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(setup): add CodeBuddy and Qoder coding-agent integrations by @magyargergo in #2368 
 feat: full Codex support — hooks, plugin marketplace, and setup ( #2328 , supersedes #1131 ) by @magyargergo in #2369 
 fix: proxy-blocked installs survive onnxruntime-node postinstall and self-heal embeddings ( #2370 ) by @magyargergo in #2372 
 fix: surface real FTS extension LOAD errors and self-heal broken extension files ( #2374 ) by @magyargergo in #2375 
 fix(lbug/mcp): exact symbol content + 0-based line storage with 1-based MCP display ( #2377 , #2379 ) by @magyargergo in #2380 
 fix(fts): diagnose Windows FTS missing-dependency load failures ( #2374 , Phase 1) by @magyargergo in #2383 
 fix: report custom HTTP embedding endpoint failures instead of huggingface download errors ( #2385 ) by @magyargergo in #2386 
 fix(lbug): recognize Windows missing-shadow error so serve repo-switch recovers ( #2382 ) by @magyargergo in #2387 
 fix: resolve imported/composed FastAPI route path constants ( #2391 ) by @magyargergo in #2393 
 fix(ci): shard platform-sensitive matrix + spawn built CLI to fix Windows cross-platform timeout by @magyargergo in #2394 
 fix(hook): emit MCP query hint when server owns DB lock ( #2396 ) by @magyargergo in #2397 
 feat: gate Icebug community engine prototype by @azizur100389 in #2376 
 fix(web): improve repository dropdown search by @evander-wang in #2381 
 fix: surface incremental dirty state diagnostics by @koriyoshi2041 in #2410 
 fix: make large incremental writebacks commit reliably ( #2409 ) by @magyargergo in #2425 
 fix(cli): actionable diagnostics for non-4K page-size buffer manager failures by @vlisitskii in #2424 
 fix(tree-sitter): recover declarations after embedded NUL bytes by @magyargergo in #2430 
 fix(web): use repo path identity in switcher by @koriyoshi2041 in #2420 
 fix: stop Napi::Error SIGABRT on analyze — index C++ type lookups, terminate workers only at JS-safe points ( #2432 ) by @magyargergo in #2436 
 
 New Contributors 
 
 @vlisitskii made their first contribution in #2424 
 
 Full Changelog : v1.6.9...v1.6.10-rc.20