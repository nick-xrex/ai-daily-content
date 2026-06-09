---
id: inbox_00939241
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.38"
author: "ruvnet"
published_at: 2026-06-08T12:52:49+00:00
fetched_at: 2026-06-08T18:00:51.511984+00:00
content_hash: "bf2cf008a8e237be4591a0a483fa553802054499deef8a460da7f46729262186"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.38 — CI/witness/security cluster fixes

Three HIGH-severity verification-cluster fixes from #2311 , #2274 , #2312 , and #2275 . 
 Fixed 
 #2311 — @claude-flow/security standalone TypeScript build (was breaking v3-ci.yml on main ) 
 integrity-verifier.ts imported @noble/ed25519 but the dep was never declared on the package itself (root override didn't propagate — same lesson as #2112 ). Added directly to v3/@claude-flow/security/package.json . Unblocks the ToolOutputGuardrail smoke (ADR-131) job and the broader pipeline outage tracked in #2275 . 
 #2274 — verify.mjs crashed on @noble/ed25519 v2 (witness integrity unverifiable) 
 verify.mjs:175 unconditionally assigned ed.etc.sha512Sync ; on the v2 patch releases that freeze etc , this throws TypeError: Cannot add property sha512Sync, object is not extensible and skips every signature check. Wrapped in if (!ed.etc.sha512Sync) plus a try/catch — sha512Sync is already wired internally on v2, so the shim is only needed on v1. Validated against macOS, Linux, and Windows manifests on this checkout: Ed25519 signature valid: yes on all three, regressed=0 missing=0. 
 #2312 — smoke-trajectory-graph-edges.mjs OOM (ADR-130 P3 job, exit 134) 
TEST 2's post-task chain ( intelligence.recordTrajectory → @ruvector/ruvllm SonaCoordinator ) blows past the default 4 GB heap. Bumped NODE_OPTIONS=--max-old-space-size=6144 on the CI step so the job completes; the underlying allocation profile in @ruvector/ruvllm is tracked as a follow-up. 
 Packages 
 
 
 
 Package 
 Old 
 New 
 Tags 
 
 
 
 
 @claude-flow/security 
 3.0.0-alpha.8 
 3.0.0-alpha.10 
 latest, alpha, v3alpha 
 
 
 @claude-flow/cli 
 3.10.37 
 3.10.38 
 latest, alpha, v3alpha 
 
 
 claude-flow 
 3.10.37 
 3.10.38 
 latest, alpha, v3alpha 
 
 
 ruflo 
 3.10.37 
 3.10.38 
 latest, alpha, v3alpha 
 
 
 
 @claude-flow/cli 's @claude-flow/security dep now pins ^3.0.0-alpha.10 so the wrapper users pick up the noble dep automatically. 
 Not in this release 
 
 #2286 — npx @claude-flow/cli@alpha --version 60s timeout is install-bandwidth + postinstall , not CLI startup. The --version fast-path has been in place since 3.10.33 (commit 4c01443 ) and exits before any heavy import. Verification harness measures cold npx -y which includes downloading the tarball + 300+ deps; nothing to fix in code. 
 #2319 — agentic-flow ./transport/loader export missing is an upstream issue ( ruvnet/agentic-flow#153 , plus a broken @fix dist-tag install). Cannot be fixed from this side until upstream lands the loader export in the stable ^2 release.