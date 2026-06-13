---
id: inbox_19c4baf8
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.44"
author: "ruvnet"
published_at: 2026-06-12T20:52:24+00:00
fetched_at: 2026-06-13T03:36:12.950030+00:00
content_hash: "513db45383d7058e0e1e27ffa756d529a105ad2a283501ed1205b66ff0c03d5a"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.44 — CI OOM fix, Windows plugin install

Patch release bundling two fixes that landed since 3.10.43. 
 Fixes 
 #2348 — break embedder-rescue mutual recursion ( #2312 ) 
 v3-ci.yml 's trajectory-graph-edges smoke had been disabled ( continue-on-error: true ) since the test process OOM'd at 4 GB on the Linux runner. Bisection ruled out the suspected SONA endTrajectory / EWC path. The actual cause was a closed cycle: 
 generateEmbedding (bridge-first)
 → bridgeGenerateEmbedding
 → agentdb.embedder.embed ← monkey-patched by rescueAgentdbEmbedder
 → generateEmbedding ← cycle closes here
 
 Microtask-driven, so no stack overflow — just monotonic heap growth to V8's limit, then SIGABRT. memory-bridge.ts 's rescueAgentdbEmbedder now delegates to a new generateLocalEmbedding export (bridge-free leaf chain) rather than the bridge-first generateEmbedding . The rescue probe is also tightened — previously it accepted any non-zero vector as "real," which the deterministic hash fallback also satisfies, so it cheerfully "rescued" a mock with another mock. New probe requires backend === 'onnx' . 
 The CI gate is re-enabled ( continue-on-error: true removed). 
 #2366 — Windows plugin install/uninstall/upgrade (community contribution) 
 On Windows, PluginManager failed every npm lifecycle command with two distinct Node failure modes: 
 
 spawn npm ENOENT — npm on Windows is a bash shim with no .exe , so execFile('npm', ...) can't resolve it. 
 spawn EINVAL — Node refuses to spawn .cmd / .bat files directly since 18.20.2 / 20.12.2 ( CVE-2024-27980 ). 
 
 All three call sites (install, uninstall, upgrade) now route through a runNpm helper that invokes cmd.exe /d /s /c npm &lt;args&gt; on Windows. POSIX path is unchanged. Argument safety is maintained by the existing validatePackageName regex gate plus Node's array-form argument quoting — security-audited for cmd.exe metacharacter injection (the version-spec characters ^ , &lt; , &gt; , = that the regex allows are inert inside Node's quoted args under cmd /s ). 
 Community PR by @danielsOink — thanks! 
 Held from this batch 
 
 #2301 (community, hive-mind --dangerously-skip-permissions ) — fix for the kebab→camel parser drop is correct on the activation half but the --no-auto-permissions deny case fails locally: the parser uses yargs-style negation ( autoPermissions: false ) which the predicate doesn't read. Comment posted on the PR with the proposed third-clause fix; will land in the next batch. 
 #2342 (vitest 1.x → 4.1.8 for GHSA-5xrq-8626-4rwp ) — CONFLICTING against current main; needs rebase + author confirmation of test-suite compatibility with the major version jump. 
 
 Install / upgrade 
 npx ruflo@latest init # 3.10.44 
npx @claude-flow/cli@latest # 3.10.44 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) and all three dist-tags ( latest , alpha , v3alpha ) verified at 3.10.44. 
 Diff 
 main...v3.10.43 — PRs #2348 , #2366 plus the release bump. 
 🤖 Generated with RuFlo