---
id: inbox_f8d562d2
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.25"
author: "ruvnet"
published_at: 2026-07-28T15:10:10+00:00
fetched_at: 2026-07-28T22:19:48.603616+00:00
content_hash: "70916c4aae6bc5752d6c4e3966515d0ff7e3bbd764e2b555d5fd103986472002"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.25 — metaharness pin-drift guard

Fixed 
 Floating @metaharness/darwin pin. distill-oracle.ts invoked npx --yes @metaharness/darwin with no version at three call sites (Tier-1 mechanical oracle), floating to npm latest — a breaking darwin release could change eval behavior mid-run. Now pinned via a single MH_DARWIN_PIN = '0.8.0' constant, declared @metaharness/darwin: ^0.8.0 in optionalDependencies as the single source of truth, and a stale ~0.3.1 doc comment corrected. Ruflo's analog of upstream agent-harness-generator#142 . 
 Added 
 metaharness pin-drift guard (the #149 analog ruflo lacked): 
 
 scripts/check-metaharness-pins.mjs — diffs each declared range ( metaharness , @metaharness/router , @metaharness/darwin ) against npm latest + a lock-step check that MH_DARWIN_PIN satisfies the darwin range. Network flakes warn, never false-positive. 
 .github/workflows/metaharness-pin-drift.yml — runs weekly + on PRs touching the pins; opens/updates a tracking issue on drift, hard-fails PRs that introduce it. 
 
 Upstream companion PRs 
 Filed against the metaharness repo: #150 (darwin pin ^0.2.2→^0.8.0, #142 ) and #151 (META_PROXY_VERSION→0.7.0 + ported pin-drift watcher, #149 ). 
 Upgrade 
 npx ruflo@latest --version # → 3.32.25 
 Refs: ADR-150, ADR-321.