---
id: inbox_f7d57342
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.7.0"
author: "ruvnet"
published_at: 2026-05-24T15:17:02+00:00
fetched_at: 2026-05-25T00:11:33.070468+00:00
content_hash: "ba682ee9c6aff3ae721f407c650564634fd39ac27138c317cba03565db513f15"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.7.0 — first stable + #2120 memory-stats legacy-DB fix

First stable release — the alpha series (3.7.0-alpha.1 → 3.7.0-alpha.81) is now closed. From here on we ship semver-stable: 3.7.0 → 3.7.1 (patch), 3.8.0 (minor), 4.0.0 (breaking). 
 Highlights 
 #2120 — memory stats / status fixed for legacy DBs 
 Reporter @alexandrelealbess on WSL2: ruflo memory stats reported Total Entries: 0 against a 251-row .swarm/memory.db , and ruflo status falsely reported "not initialized". 
 
 
 
 Fix 
 Where 
 
 
 
 
 Accept status IS NULL alongside 'active' 
 memory-bridge.ts bridgeListEntries 
 
 
 Same in raw sql.js fallback 
 memory-initializer.ts listEntries (4 prepares) 
 
 
 Backfill UPDATE ... SET status='active' WHERE status IS NULL 
 memory-initializer.ts ensureSchemaColumns 
 
 
 isInitialized() now accepts any of .claude-flow/config.{yaml,json} , .swarm/memory.db , .claude/settings.json 
 status.ts 
 
 
 New CI smoke smoke-memory-stats-legacy-db.mjs 
 .github/workflows/v3-ci.yml 
 
 
 
 Versioning policy change 
 
 No more -alpha.N releases. Default npm publish tag is latest . 
 Legacy alpha and v3alpha dist-tags continue to point at the latest stable for backward compat — so npx ruflo@alpha and npx claude-flow@v3alpha still work. 
 
 CI surface (all guards added on alphas, still active) 
 5 new regression smokes from the alpha series: 
 
 smoke-agent-execute-providers.mjs ( #2042 ) 
 smoke-github-safe-injection.mjs + smoke-github-actions-pins.mjs + smoke-deprecated-actions.mjs ( #2089 ADR-127) 
 smoke-attribution-opt-in.mjs ( #2089 ADR-127) 
 smoke-init-bundle-invariants.mjs ( #2095 ADR-128) 
 smoke-ruvllm-wasm-auto-init.mjs ( #2086 ) 
 smoke-memory-stats-legacy-db.mjs ( #2120 , this release) 
 
 Try it 
 npx ruflo@latest init # → 3.7.0 
 # or upgrade in place 
npm i -g ruflo@latest 
 Changelog 
 See git log v3.7.0-alpha.71...v3.7.0 for the full alpha series. Key fixes that culminated in this release: 
 
 #2120 (alpha.81 → 3.7.0) — memory stats legacy DB NULL status 
 #2110 (alpha.80 → alpha.81) — WSL2 daemon triple bug 
 #2112 (alpha.79 → alpha.80) — opentelemetry overrides on ruflo wrapper 
 #2086 (alpha.71 → alpha.72) — ruvllm WASM auto-init 
 #2042 (alpha.77 → alpha.78) — agent_execute provider routing 
 #2078 (alpha.78) — opt-in Co-Authored-By trailer 
 #2089 / ADR-127 — GitHub stack modernization 
 #2095 / ADR-128 — init bundle reduce 
 #2068 / ADR-126 — neural-trader substrate integration 
 #2061 / ADR-125 — memory consolidation, 2.70x retrieval speedup via RaBitQ quantization 
 
 Co-Authored-By: rUv