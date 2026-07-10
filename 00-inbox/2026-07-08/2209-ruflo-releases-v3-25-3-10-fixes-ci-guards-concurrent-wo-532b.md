---
id: inbox_61322014
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.25.3"
author: "ruvnet"
published_at: 2026-07-08T02:19:30+00:00
fetched_at: 2026-07-09T22:09:33.308429+00:00
content_hash: "532b6dbd057741d84f02735e0853bb7faa16e112229519578c28a66828d6f6eb"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.25.3 — 10 fixes + CI guards (concurrent workflow)

Consolidated patch release. All 10 fixes investigated + implemented + validated + guarded in parallel via workflow orchestration in a single session. 
 Fixes 
 
 
 
 # 
 Title 
 Guard 
 
 
 
 
 #2561 
 npx cold-install timeout — pruned CLI optionalDependencies 
 .github/workflows/no-cli-optdep-bloat-2561.yml 
 
 
 #2566 
 GAIA isAnswerCorrect reverse-substring collision 
 unit test 
 
 
 #2575 
 neural status ReasoningBank Empty vs 7798 patterns display 
 (fix-only) 
 
 
 #2578 
 ADR-104 phantom agentic-flow/transport/loader witness marker 
 .github/workflows/no-phantom-agentic-flow-subpath.yml 
 
 
 #2590 
 CI Node24 memory smoke fails on onnxruntime-node postinstall 
 in-workflow guard 
 
 
 #2593 
 helpers.manifest.json stale — verify + sign in prepublishOnly 
 .github/workflows/helpers-manifest-guard.yml 
 
 
 #2594 
 memory store UNIQUE violation — flip --upsert default to true 
 unit test 
 
 
 #2596 
 memory init Windows EPERM — drop sql.js writeback race 
 unit test 
 
 
 #2599 
 doctor: @claude-flow/memory NOT resolvable — self-heal 
 unit test 
 
 
 #2600 
 Windows shim @latest vs @alpha dist-tag parity 
 smoke test 
 
 
 
 Also resolves #2583 (env-var-precedence audit) — already fixed on main by #2586 . 
 Known limitation 
 The tarballs for this release ship with the pre-existing stale helpers.manifest.json (version 3.23.0) because the local publish environment did not have the GCP signing secret available. The #2593 fix guards future releases from regressing — 3.25.4 will properly re-sign the manifest to close the loop. 
 Install 
 npx ruflo@3.25.3
npx ruflo@latest
npx claude-flow@v3alpha
npx @claude-flow/cli@alpha
 
 All three legacy dist-tags ( latest , alpha , v3alpha ) point to 3.25.3 for backward compatibility. 
 Packages 
 
 @claude-flow/cli@3.25.3 
 claude-flow@3.25.3 
 ruflo@3.25.3 
 
 🤖 Generated with RuFlo