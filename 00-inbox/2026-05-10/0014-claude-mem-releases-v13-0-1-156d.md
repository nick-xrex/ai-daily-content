---
id: inbox_b4aa386a
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.0.1"
author: "thedotmack"
published_at: 2026-05-10T07:26:31+00:00
fetched_at: 2026-05-26T00:14:50.184293+00:00
content_hash: "156dd9c17b0d7d97f2303bd16ac8bf96dfc7859545c61d96e697fc5d711e716d"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.0.1

Bug fixes 
 MCP server 
 
 #2371 — drop ${_R%/} parameter-expansion trim in .mcp.json that tripped Claude Code's MCP validator 
 
 Environment isolation 
 
 #2357 — block ANTHROPIC_BASE_URL leak; use a three-branch OAuth-skip predicate 
 Add CLAUDE_MEM_ENV_FILE lazy resolver so tests (and multi-profile users) can redirect the env-file path without module-load-order constraints 
 
 Worker lifecycle 
 
 Classify Claude SDK HTTP 400 as unrecoverable so the worker stops retrying a doomed request 
 Stop hook crash hardened: onclose handler now performs background tree-kill on unexpected subprocess exit 
 
 Chroma 
 
 #2313 — enforce a single chroma-mcp subprocess per worker (singleton via disposeCurrentSubprocess() on every code path; tree-kill of orphans on dispose) 
 Pin onnxruntime&gt;=1.20 and protobuf&lt;7 to fix INVALID_PROTOBUF on macOS arm64 
 
 Build 
 
 Polyfill import.meta.url to pathToFileURL(__filename) in the CJS worker bundle so ESM-style code resolves correctly (CodeRabbit-driven follow-up) 
 
 Tests / review 
 
 tests/env-isolation.test.ts no longer mutates the real ~/.claude-mem/.env ; OAuth spy wrapped in try/finally to avoid leaks across runs 
 3 new chroma-mcp regression tests for #2313 (singleton enforcement) 
 
 Misc 
 
 Daily dependency bump per CLAUDE.md maintenance policy 
 
 Full diff: #2394