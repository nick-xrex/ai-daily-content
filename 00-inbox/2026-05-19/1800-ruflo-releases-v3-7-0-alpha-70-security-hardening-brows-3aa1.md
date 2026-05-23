---
id: inbox_cfa85c58
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.70"
author: "ruvnet"
published_at: 2026-05-19T21:03:17+00:00
fetched_at: 2026-05-22T18:00:34.012787+00:00
content_hash: "3aa12034cbe3cd54b3f19dc275fc1591e9c42597ae2c0a3f5d15b35f9032cfe3"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.7.0-alpha.70 — Security hardening + Browser substrate + Graph Intelligence

TL;DR — This release ships two coordinated security fixes (a real Ed25519 verifier on the plugin registry, and a Windows ONNX crash fix), the new Browser substrate (ADR-122) for trustworthy agent automation, the new RuFlo Graph Intelligence Engine plugin (ADR-123) for sublinear-time program analysis, and a 5-layer supply-chain audit that took the root package's CVE count from 13 HIGH/CRITICAL to zero . 
 
 Install / upgrade: 
 npx ruflo@latest # umbrella CLI 
npx claude-flow@latest # legacy umbrella 
npx @claude-flow/cli@latest 
 
 🔐 Security (please read) 
 Plugin registry signature verification is now real (CWE-347, #1922 ) 
 The plugin registry's Ed25519 signature verifier was a stub — it returned true whenever the served registryPublicKey field started with "ed25519" . With requireVerification: true (the default) a network adversary on the path to an IPFS gateway could swap the registry and have a user install attacker-mapped plugin tarballs running with filesystem + network + hooks permissions. 
 Fixed in this release (PR #2060 , thanks to @aaronjmars for the disclosure + patch): 
 
 Real Ed25519 verification using the verifier that already lived at transfer/ipfs/client.ts:325 . 
 Verifier pins to the caller-supplied trusted public key from DEFAULT_PLUGIN_STORE_CONFIG , NOT the self-asserted registryPublicKey (which an attacker could swap too). 
 Call site now await s and fails closed (falls back to the local demo registry instead of warning-and-continuing). 
 New plugin-registry-signature-smoke CI job locks the invariant for every future PR — including PRs from forks now that the pull_request trigger covers [main, develop] . 
 
 If you've installed plugins from anywhere other than the official Pinata registry on a network you don't fully trust between alpha.69 and now, take a look at what's installed. 
 Windows ONNX binding crash ( #2048 ) 
 import('agentic-flow/reasoningbank') crashed on Windows even with VCRedist installed, because router/providers/onnx-local.ts did a top-level await import('onnxruntime-node') that forced the native binding to load at module-import time, before any user code ran. 
 Fixed : agentic-flow@2.0.13 (upstream PR ruvnet/agentic-flow#155 ) moves the import into a lazy loadOrt() helper called from initializeSession() . The binding now loads only when an explicit inference call happens. This release bumps agentic-flow ^2.0.12 → ^2.0.13 in the root and v3/@claude-flow/browser (PR #2056 ). 
 Supply-chain hardening ( #2046 ) 
 A new 5-layer audit pipeline ( scripts/audit-supply-chain.mjs ) runs on every PR: 
 
 CVE audit with per-package allowlist for triaged-and-tracked findings. 
 Lockfile integrity — every dep must carry a SHA-512 hash. 
 Top-level allowlist — new top-level deps require explicit approval. 
 Typosquat reject — blocks known typo-named packages. 
 Publisher trust snapshot — every release records which npm account published each dep, so silent maintainer takeovers leave a paper trail. 
 
 Backed by GitHub's dependency-review-action , a CODEOWNERS review gate on any change to allowed-deps, and 14 npm-overrides that pinned 13 HIGH/CRITICAL CVEs out of the dependency graph. Root npm audit now reports 0 vulnerabilities (was 13). 
 Pre-bash hook silent-swallow ( #2017 ) 
 The pre-bash PreToolUse safety hook (which is supposed to refuse rm -rf / , fork bombs, etc.) was exiting 0 on every dangerous payload because of an unhandled TypeError swallowed by the safety timer's outer try/catch. Fixed in alpha.45 and locked in by a new CI smoke that drives real dangerous-command shaped JSON into the hook and asserts it blocks. 
 
 🌐 New: Browser substrate ( ADR-122 , #2043 ) 
 @claude-flow/browser is now a trustworthy agent substrate , not just a Playwright wrapper. Every browser run produces a signed trajectory (an RVF container with cookie attestations + page snapshots + risk classifications) that any other agent or auditor can replay. Phases shipped: 
 
 
 
 Phase 
 Capability 
 What it gives you 
 
 
 
 
 0 
 agent-browser@0.27 + signed trajectories 
 every run is reproducible from the signed RVF 
 
 
 1 
 23 MCP tools 
 agents drive the browser directly via MCP 
 
 
 2 
 Causal recovery 
 when an agent step fails, the trajectory tells you why — not just "click failed" 
 
 
 3 
 Attested cookie vault 
 session cookies sealed against the running process identity 
 
 
 4 
 Federated MCTS 
 multiple agents can explore branches of the same web flow in parallel 
 
 
 5 
 GOAP preflight + cost-aware routing 
 agent picks the cheapest model that can plausibly finish the task 
 
 
 6 
 Session capsule + risk classes 
 replayable session container with read/write/auth-touching tagged separately 
 
 
 7 
 Workflow compiler + production-aware UCT 
 compile a recorded session into a typed automation; UCT understands prod vs dev costs 
 
 
 
 The plugin is gated through AIDefence so PII never leaves the browser sandbox unredacted. 
 Try it: 
 npx ruflo@latest plugins install @claude-flow/browser
ruflo browser session-record --task \" Sign in to staging dashboard and screenshot the kanban \" 
 
 📊 New: RuFlo Graph Intelligence Engine plugin ( ADR-123 , #2045 ) 
 A new ruflo-graph-intelligence npm package that turns sublinear-time graph algorithms ( sublinear-time-solver@1.7.0 ) into 5 practical "wedges" you can run against your codebase or PR queue: 
 
 Spectral influence — which files in a 50-service monorepo will ripple if you touch this one? 
 Cone-of-influence forensics — given a regression in service-A , which PRs in the last 30 days could have caused it? 
 Portfolio CG — given 12 candidate refactors, which set has the highest expected payoff at the lowest blast radius? 
 AIDefence threat propagation — given a leaked credential, which downstream callsites need rotation first? 
 GOAP-LP planner — when a planner has dozens of candidate actions, which sequence reaches the goal with minimum cost? 
 
 Plus a streaming bridge and signed PR artifacts so the graph state can be federated across multiple agents working in the same repo. 
 npx ruflo-graph-intelligence analyze --target ./src --wedge spectral-influence 
 Shipped with 104 tests (104/104 passing) and registered in the official plugin marketplace. 
 
 🛠️ Quality + reliability 
 
 Knowledge-graph kg-extract fix ( #2049 ) — TypeScript import type and value imports were being conflated, producing phantom runtime cycles. Now classified as separate type-depends-on (weight 0.1) and depends-on (weight 1.0) relations. Locked in by scripts/smoke-kg-extract-type-imports.mjs . 
 agentic-flow@2.0.12 upstream patch ( ADR-124 ) — @xenova/transformers moved from dependencies to optionalDependencies so installs that don't need embeddings can --omit=optional for a clean CVE-free tree. 
 Witness manifest CI guards ( #2021 ) — refreshes stale markers, regenerates the signed manifest, and adds a fast drift-only check that runs on every push (no full build needed). 
 Standalone module READMEs ( #2022 , alpha.43+44) — @claude-flow/memory , @claude-flow/embeddings , @claude-flow/security are now usable as standalone packages with their own usage docs + npm download badges. 
 Memory subsystem consolidation ADR proposed ( ADR-125 ) — Roadmap for the next memory release: single canonical MemoryService API, real HybridBackend default, persistent HNSW (no rebuild on cold start), MemoryConsolidator service, graceful retrieval degradation with FTS5 fallback, runnable benchmarks. Proposed in this release; first delivery PR coming next. 
 
 
 🔄 Migration / upgrade notes 
 Most users: no action required, just npx ruflo@latest . 
 If you import @claude-flow/browser programmatically : the new MCP tools (23 of them) are additive — existing imports continue to work, but you'll want to look at the new browser_session_record / browser_session_replay / browser_template_apply MCP tools for the trajectory + session-capsule features. 
 If you install plugins from a custom IPFS gateway : signature verification is now strict and fails closed. If your custom registry isn't properly Ed25519-signed against the pinned trusted key, it will fall back to the demo registry. See the new contract in v3/@claude-flow/cli/src/plugins/store/discovery.ts:verifyRegistrySignature . 
 If you run on Windows and previously hit the onnxruntime_binding.node is not a valid Win32 application error: upgrade and try again. If you still hit it, you're explicitly running ONNX inference; npm install --omit=optional will skip the binding entirely and the embedding paths fall back to hash-based. 
 
 📦 Published packages (npm) 
 
 
 
 Package 
 Version 
 Tags 
 
 
 
 
 @claude-flow/cli 
 3.7.0-alpha.70 
 alpha , latest , v3alpha 
 
 
 claude-flow 
 3.7.0-alpha.70 
 alpha , latest , v3alpha 
 
 
 ruflo 
 3.7.0-alpha.70 
 alpha , latest 
 
 
 
 📜 PRs merged since alpha.44 
 
 #2060 — CWE-347 plugin registry signature verification (closes #1922 ) 
 #2056 — agentic-flow ^2.0.12 → ^2.0.13 Windows ONNX lazy-load (closes #2048 ) 
 #2055 — kg-extract type-import classifier + CI guard (closes #2049 ) 
 #2050 — 5-layer supply-chain audit + dependency-review + CODEOWNERS (closes #2046 ) 
 #2045 — RuFlo Graph Intelligence Engine plugin (ADR-123, closes #2044 ) 
 #2043 — Browser substrate beyond SOTA (ADR-122, closes #2041 ) 
 #2022 — Standalone-use recipes + npm download badges (alpha.43+44) 
 #2052 — Remove duplicate lowercase skill.md files 
 #2051 — Register ruflo-graph-intelligence in marketplace manifest 
 
 Full diff : v3.7.0-alpha.44...v3.7.0-alpha.70 
 
 🙏 Special thanks to @aaronjmars for the responsible disclosure + clean patch on #1922 , and the careful follow-up on the dependency-CVE backlog.