---
id: inbox_1d05d1bf
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.24.0"
author: "ruvnet"
published_at: 2026-07-05T15:40:32+00:00
fetched_at: 2026-07-05T22:00:17.102992+00:00
content_hash: "07ff408e74879fa371b820a550ca9a9aaf83ecd61f7435f30443413e10f217d6"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.24.0 — Self-Learning Flywheel

ruflo 3.24.0 — The Self-Learning Flywheel 
 ruflo can now improve one of its own operating policies over time and prove each improvement is real — not marketing. Merges #2572 (ADR-176 self-optimizing flywheel + ADR-177 signed config propagation). 
 📖 Full write-up (plain language + technical + usage + upgrade notes): https://gist.github.com/ruvnet/f8e2851fd307df5d5de7b5c70c37fa0c 
 What's new 
 
 Verified retrieval improvement, auto-applied to every install. A signed config champion (Ed25519 + RVFA) is adopted on startup, fail-closed on authenticity and suitability. Better retrieval defaults out of the box, +0.0738 nDCG@3 over the previously-tuned baseline. No re-init needed. 
 Self-optimizing flywheel (opt-in, $0 default). The background daemon compounds verified retrieval-policy improvements: each generation reads the persisted champion as baseline, gates a candidate on a frozen held-out with a significance test ( accept/v1+sig ) + human-relevance guard + a separate canary, and on promotion advances the champion so the next tick builds on it. Winners accumulate into a signed, independently-replayable lineage back to an immutable root (git-for-operating-policies). 
 Shadow-first / no auto-serve + drift canary. Promoted champions serve only after a one-generation shadow delay; a canary re-scores on the evolving store each tick and auto-rolls-back regressions. 
 Meta-learning. The optimizer biases its search toward policy axes with measured historical payoff. 
 Proof, not assertion. Receipt bundles replay independently without trusting our logs ; a CI guard keeps the shipped evidence valid on every PR. 
 
 Demonstrated live: two real, significant, compounding promotions (self-retrieval RR 0.496 → 0.758 → 0.847 ), human relevance preserved, zero human intervention. 
 
 Honest scope: the flywheel's compounding gains are on a self-supervised retrieval benchmark, gated so human-labeled relevance does not regress — not a claim that human relevance improved generation-over-generation (held flat by design). The auto-applied one-shot champion was tuned on human-labeled relevance. 
 
 Upgrade 
 npx ruflo@latest # or npx ruflo@3.24.0 
 Backwards-compatible / additive · signing keys unchanged · the flywheel is off unless RUFLO_HARNESS_LOOP=1 . 
 Packages: @claude-flow/cli@3.24.0 · claude-flow@3.24.0 · ruflo@3.24.0 
 🤖 Generated with RuFlo