---
id: inbox_6cffca54
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.8.0"
author: "ruvnet"
published_at: 2026-05-24T22:33:10+00:00
fetched_at: 2026-05-25T00:11:33.057746+00:00
content_hash: "b24645818d9785fef699c0b4ec64232b4c315a7d92cca55dbe508a903d23a522"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.8.0 — ADR-129 rvagent full integration

Highlights 
 ADR-129 — Full rvagent integration (PR #2123 ) 
 
 16 new MCP tools for WASM agent gallery &amp; introspection (10 CRUD + 6 query) 
 wasm_agent_compose with addMcpTools bridge unlocking all 314 MCP tools to WASM agents 
 JsModelProvider real provider routing (replaces the echo-stub bypass) 
 Plugin contract : rvagent field on plugin manifest + includePlugins option in compose 
 
 Fixes 
 
 #2120 — getBridge() now honors CLAUDE_FLOW_DISABLE_BRIDGE=1 , fixing the legacy-DB status backfill regression that caused ruflo memory stats to report 0 entries against pre-status-column databases 
 
 Performance (PR #2124 — SOTA comparator benchmarks) 
 4 production speedups on wasm_agent_compose hot path (all in wasm-agent-tools.ts ): 
 
 Plugin manifest cache — 21-plugin overhead: 0.196ms → 0.001ms 
 isDestructiveTool fast-path — suffix check before 8-regex battery 
 Hoisted Buffer import — eliminates await import('node:buffer') microtask per call 
 Memoized loadAgentWasm() — module-level promise singleton for all 20 MCP handlers 
 
 Cumulative compose_50_tools: 0.351ms → 0.146ms (2.4× improvement) 
 Verified SOTA matrix vs LangGraph 1.2.1, AutoGen 0.4.9, CrewAI 0.80.0 on darwin-arm64 + linux-x64: 
 
 
 
 Dimension 
 ruflo 
 AutoGen 
 LangGraph 
 CrewAI 
 
 
 
 
 Cold start 
 3.93ms 
 185ms 
 534ms 
 2527ms 
 
 
 Single turn 
 0.012ms 
 6.13ms 
 37.1ms 
 proxy† 
 
 
 N=10 parallel 
 1.27ms 
 61ms 
 393ms 
 proxy† 
 
 
 RSS 
 61.6MB 
 78.7MB 
 80.3MB 
 265.7MB 
 
 
 
 † CrewAI dispatch proxied (requires real LLM). 
 Full methodology, Linux numbers, concurrency scale, v3.7→v3.8 delta: https://gist.github.com/ruvnet/298f8c668c8859b369f91734a0e9cbbe 
 Benchmarks (5-trial median, bench-rvagent.mjs ) 
 
 Provider routing: 0.025ms (fake key, router only) 
 Compose 100 tools: 0.215ms 
 Gallery CRUD cycle: 0.094ms 
 Plugin enum (absent): 0.035ms 
 
 Witness manifest — ADR-129 P1–P4 fix entries registered ( verification/witness-fixes.json , 117/117 verified) 
 Install 
 npx ruflo@latest # or @3.8.0 / @alpha / @v3alpha 
npx claude-flow@latest
npx @claude-flow/cli@latest 
 🤖 Generated with RuFlo