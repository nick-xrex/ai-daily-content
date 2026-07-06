---
id: inbox_ce185e40
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.25.0"
author: "ruvnet"
published_at: 2026-07-05T17:33:28+00:00
fetched_at: 2026-07-05T22:00:17.100759+00:00
content_hash: "1b07ace66341009fcee65ba7f899bc02d89105b07a08eda73125e8b1efff2281"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.25.0 — Anti-overfitting proofs + Lattice embedder tier

ruflo 3.25.0 — Anti-overfitting proofs (+ an inactive Lattice embedder seam) 
 Anti-overfitting ( #2580 ) — real, shipped 
 
 Frozen public human-labeled eval set ( .claude/eval/human-relevance-frozen-v1.json ) — hash-pinned, tamper-evident; the red/blue anchor the flywheel must never regress. 
 Per-generation human-relevance deltas in every receipt ( deltas.humanRelevance ) — so "self-retrieval up, human relevance flat → OVERFITTING" is visible in flywheel status , not hidden. 
 Clean-room replay acceptance test ( scripts/replay-generation.mjs ) — replay a promoted generation from its receipt alone: identical hashes, re-run accept/v1+sig , offline (network trapped). Wired into CI. 
 
 ⚠️ Correction — the "Lattice WASM embedder tier" ( #2581 ) is INACTIVE 
 The earlier notes for this release overstated it. There is no @ruvector/lattice-wasm package (npm 404), and no "Lattice" embedder package exists in the ruvector ecosystem. What shipped is a fail-closed, optional adapter seam that dynamically imports an (env-configurable) package name and degrades to ruvector-ONNX → hash when it is absent — which it always is today. It is therefore dormant / no-op and causes no regression, but it is NOT a working multi-model embedder. The models referenced (bge / qwen3-0.6b / paraphrase-miniLM) exist only in a Rust ONNX example, not a publishable package. A follow-up will either remove the seam or wire it to a real embedder. 
 Net for users: upgrade for the anti-overfitting proofs; embeddings behave exactly as in 3.24.0 (ruvector ONNX where available). 
 Additive · backwards-compatible · fail-closed. npx ruflo@latest .