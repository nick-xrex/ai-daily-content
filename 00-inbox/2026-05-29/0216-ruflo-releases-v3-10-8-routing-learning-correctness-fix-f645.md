---
id: inbox_3a6f7943
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.8"
author: "ruvnet"
published_at: 2026-05-29T17:04:29+00:00
fetched_at: 2026-05-30T02:16:29.846303+00:00
content_hash: "f6458741f06d810472daad7935bc8755301369b7a883491176df2f519c5d9f24"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.8 — routing-learning correctness fixes

Ruflo v3.10.8 — routing-learning correctness fixes 
 Two follow-up fixes from the intelligence audit's remaining punch-list ( docs/reviews/intelligence-system-audit-2026-05-29.md ). 
 Bug B — stale route cache hid learning 
 QLearningRouter.update() only invalidated the whole route cache every 50 updates, so a freshly-learned Q-update stayed hidden behind a stale cached decision — feedback appeared to have no effect on routing in-process until 50 updates accumulated. Now the updated state's cache entry is invalidated immediately. Verified: learned route flips coder→researcher within 10 updates. 
 Bug C — --explore false was ignored 
 Boolean flags dropped an explicit space-form value, so a default-true boolean ( explore ) stayed true even with --explore false — exploitation could not be forced. The parser now consumes a true / false literal for boolean flags ( --explore false , -e false ); --explore=false and --no-explore keep working. Verified: deterministic exploitation with explore=false . 
 Deferred (documented in the audit, not patched) 
 
 SONA default-path: re-examined — the default path already learns via LocalSonaCoordinator ; the inert piece is a non-load-bearing supplementary forward. 
 WASM MicroLoRA apply() inert — lives in the @ruvector/ruvllm dependency (needs upstream fix). 
 Per-task bandit priors — changes a persisted schema (needs an ADR + migration). 
 
 All three packages published at 3.10.8 ( latest / alpha / v3alpha in lockstep). CI: 31/31 green. 
 🤖 Generated with RuFlo