---
id: inbox_89203bda
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.33"
author: "ruvnet"
published_at: 2026-06-02T08:00:19+00:00
fetched_at: 2026-06-03T00:30:05.660700+00:00
content_hash: "d863c64b06aaedd7a3733d44eb1440ff57830eaa15427bda9de2ae8b3aa6f10d"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.33 — CI/router/ONNX bug cluster

v3.10.33 — CI/router/ONNX bug cluster 
 Critical / high-severity fixes from open issues 
 #2267 [HIGH] — v3-ci.yml 5 consecutive failures on main 
 
 Root cause: unquoted : inside a step name ("Guard 2 — smoke: generate ...") — YAML parser treated smoke: as a second mapping key and rejected the whole workflow. GitHub Actions accepted the push, scheduled the run, and produced zero jobs — invisible to green-dashboard-style monitoring. 
 Fix: quote the name. Workflow now parses to 53 jobs. 
 
 #2256 [HIGH] — --version blocks 60+ s on cold ONNX cache 
 
 Root cause: --version triggered the full CLI bootstrap, which eagerly loaded ruvector + downloaded a 23 MB ONNX model from HuggingFace. Cold-cache cost: ~60–90 s wall time, causing SIGTERM (exit 143) under the default npx and 30 s MCP stdio timeouts. 
 Fix: short-circuit --version / -V in both @claude-flow/cli/bin/cli.js and ruflo/bin/ruflo.js before any heavy import — read version straight from package.json . 
 Measured: 60s+ → 33 ms against the published ruflo@3.10.33 . 
 
 #2253 [Critical] — MCP stdio writes non-JSON to stdout, times out in Codex 
 
 Root cause: upstream embedder libraries ( ruvector , ruvector-onnx-embeddings-wasm ) emit progress to console.log (stdout) with messages like Loading model: ... , Downloading: ... , 🚀 Initializing N worker threads... . That corrupts the MCP JSON-RPC stdio framer; strict clients like Codex never see initialize complete. 
 Fix: log-filters.ts now redirects all known embedder progress prefixes from console.log → console.error . Filter installed in both bin/cli.js (covers MCP stdio path) and src/log-filters.ts (CLI path). 
 Verified end-to-end : echo '{"jsonrpc":"2.0",...}' | npx ruflo now returns clean JSON-RPC on stdout with all ONNX noise routed to stderr. 
 
 #2257 [High] — .claude/helpers/router.js mis-routes at 80% confidence via unanchored regex 
 
 Root cause: keyword patterns like cd / ci / ui / add / structure matched inside unrelated words: decision / infrastructure / address / addendum . Confidence was a hardcoded 0.8 despite the matcher being a static keyword table, not a learned classifier. 
 Fix: token-list schema with \b boundaries on single tokens (phrases keep whitespace as a natural boundary). Matched-confidence 0.8→0.6, fall-through 0.5→0.3 to reflect the heuristic-not-learned nature. 
 Validated against all 11 reported mis-route cases plus the source-of-truth generator output. 
 
 Already fixed (waiting for this publish) 
 #2246 — memory_search_unified 6-namespace hardcode 
 
 Already fixed in source (3.10.29, ADR-089). Reporter's environment was 3.10.22. Dynamic namespace enumeration now ships in 3.10.33. 
 
 Not a code bug 
 #2243 — verify.mjs cannot load @noble/ed25519 
 
 Script already handles missing dep with a clear Fix: ... message and exits 2 (precondition failure). Confirmed signatureValid=true on a clean checkout. Operational fix belongs in the external scheduled runner's config (must npm ci before invoking verify.mjs). 
 
 Out of scope 
 #2259 — memory store/list contradictory persistence surfaces 
 
 Architectural fix in memory-bridge.ts dispatch; tracked separately. 
 
 CI regression guards (so this can't happen again) 
 
 scripts/smoke-workflows-yaml.mjs — parses every .github/workflows/*.yml and fails the build on any YAML syntax error. Direct guard against the #2267 silent-fail mode. 
 scripts/smoke-router-regex.mjs — renders the router from helpers-generator.ts::generateAgentRouter , asserts all 11 mis-route cases pass, confidence isn't 0.8, and \b anchors are still in the source. 
 New static-regression-guards job runs both smokes early in v3-ci.yml (no install/build — just js-yaml + tsx ). 
 
 Install 
 npx ruflo@latest --version # → ruflo v3.10.33 (33 ms) 
npx @claude-flow/cli@latest --version # → ruflo v3.10.33 (35 ms) 
 All three dist-tags ( latest , alpha , v3alpha ) point at 3.10.33 across all three packages.