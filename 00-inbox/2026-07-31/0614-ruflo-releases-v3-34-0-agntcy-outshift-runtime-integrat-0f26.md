---
id: inbox_e5062722
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.34.0"
author: "ruvnet"
published_at: 2026-07-31T16:04:41+00:00
fetched_at: 2026-08-01T06:14:51.048049+00:00
content_hash: "0f26efc2da507a658a70e9af7cca869a07785944622bbf376eac25885d98b561"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.34.0 — AGNTCY/Outshift runtime integration

AGNTCY/Outshift runtime integration (ADR-378/379/380) 
 Optional, removable augmentation per ADR-150's pattern — the kernel stays fully 
operational with these packages absent. 
 
 New CLI verbs : ruflo transport use slim , ruflo agent publish , ruflo swarm join &lt;namespace&gt; . 
All exit 0 with a clear message when RUFLO_AGNTCY_SLIM_ENDPOINT is unset — no fake success paths. 
 CASA (Continuous Agentic Semantic Authorization) — deterministic free-text-objective → 
bounded allow/deny/budget/expiry envelope compiler, deny-by-default enforcement gate, 
Ed25519-signed decision receipts ( .swarm/casa-receipts.jsonl ). 
 AGNTCY OTel span attributes — coordination.episode , authorization.decision . 
 Companion Rust crate v3/crates/ruflo-agntcy mirrors the TS enforcement logic (real 
in-process LocalTransport , SlimTransport stub behind a non-default slim Cargo feature). 
 Companion package @metaharness/agntcy 
(build-time half — identity, OASF export, Directory publish, semantic observability) published 
for the first time from the sibling metaharness repo. 
 See it in action: AGNTCY showcase — a real trace 
and the presentation deck . 
 
 npm Trusted Publishing release workflow (ADR-378) 
 .github/workflows/stable-npm-release.yml publishes the three-package stable train 
( @claude-flow/cli , claude-flow , ruflo ) from an immutable, tag-pinned checkout with a full 
test/build/pack/install smoke-test gate before any registry write, verifies published-package 
integrity against the locally-built archive, and rolls out latest / alpha / v3alpha dist-tags 
together. This release is the first real run of that workflow. 
 Fixed 
 
 @agntcy/slim-bindings pinned to the confirmed-working alpha ( 2.0.0-alpha.5 ) — the SLIM 
maintainers moved off uniffi-bindgen-react-native (incompatible with plain Node) onto 
 @ubjs/core / @ubjs/node ; verified live end-to-end. 
 security scan failed open on unvalidated --depth / --type / --target — all three now fail 
closed before anything is scanned or written. 
 
 Changed / Removed 
 
 security scan --depth full deprecated (normalises to deep with a warning). 
 security scan --type container now rejected instead of silently reporting clean ( breaking 
for pipelines passing --type container ). 
 
 Full changelog: CHANGELOG.md 
 
 Install: npx ruflo@latest doctor · npx ruflo@latest agent publish --help