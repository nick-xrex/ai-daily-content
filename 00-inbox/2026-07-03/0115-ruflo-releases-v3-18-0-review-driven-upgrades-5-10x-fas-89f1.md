---
id: inbox_793a827e
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.18.0"
author: "ruvnet"
published_at: 2026-07-03T21:01:34+00:00
fetched_at: 2026-07-04T01:15:53.880853+00:00
content_hash: "89f1e0259afac75ffdcda2c68998f4bc0c502cc884c67c5835e0427d704214f0"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.18.0 — Review-driven upgrades: 5-10x faster CLI, supply-chain hardening, GAIA integrity family, SOTA capabilities

Two merged feature trains, driven by a 4-review audit (SOTA research + performance + architecture + security) implemented by six concurrent agents. 
 Performance 
 
 CLI startup 5–10x faster — lazy ONNX embedder init removed a 450–2,800ms tax from every command ( --help 0.50s → 0.09s, whole CLI back under the &lt;500ms target) 
 Batch embeddings in memory import (200-entry import: 1220ms → 115ms), local-first ruvector resolution, metaharness skills now resolve from a pinned versioned cache ( score 0.35s, zero registry traffic) 
 
 Security 
 
 Killed third-party npx metaharness@latest (supply-chain HIGH) — pinned versioned-cache resolution with graceful degradation intact 
 OTel floor-became-ceiling overrides lifted (root npm audit --omit=dev : 30 → 0 ); grpc-js / hono / brace-expansion GHSAs cleared 
 CodeQL high fixed: polynomial ReDoS in A2A card slugify (remote input) → linear scan 
 
 GAIA integrity family (ADR-167 / 168 / 169) 
 
 ADR-167 : pre-submission exploit audit (AUD-1..10) + signed earning-integrity attestation — signing proves bytes; the audit proves the score was earned. Honest harness_gap skips where the harness can't yet supply evidence 
 ADR-168 : harness evidence recording (trajectories, tool names+args, split provenance, signed judge cache) — the forward contract that turns those skips enforceable ( #2548 ) 
 ADR-169 : benchmark reporting integrity standard — strict-EM headlines, view-labeled scaling arms, disclosed no-work/empty rates, mandatory reproducibility blocks 
 
 New capabilities 
 
 hooks_model-verify — confidence-gated tier escalation ($0 structural verifier; route → generate → verify → escalate; feeds the routing bandit) 
 Temporal validity on hierarchical memory (validFrom/validUntil + supersede-on-conflict, Zep/Graphiti-style) 
 A2A Agent Cards (spec 1.0.0) — federation discovery interop at /.well-known/agent-card.json , ADR-166 bind posture preserved 
 Execution-state-tree trajectory retrieval prototype (MAGE-style) behind strategy: "state-tree" 
 metaharness evolve --diagnose — GEPA failure-class diagnosis 
 Browser session recording fixed end-to-end (trajectory flags were invalid on every prior ruvector version) 
 
 Validation 
 tsc clean · MCP contract 171/171 (15 metaharness tools) · plugin smoke 122/122 · memory 442/442 · federation 600/600 · root audit 0 vulnerabilities · CI fully green on merged main (incl. the #2552 lockfile hotfix that had 25 main jobs red) 
 PRs: #2543 , #2547 , #2552 · Issues: #2542 , #2548 · Previous: v3.17.0 (metaharness learn + gepa)