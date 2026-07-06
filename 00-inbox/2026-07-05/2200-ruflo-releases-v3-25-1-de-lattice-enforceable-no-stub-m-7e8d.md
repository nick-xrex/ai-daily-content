---
id: inbox_35151944
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.25.1"
author: "ruvnet"
published_at: 2026-07-05T18:11:04+00:00
fetched_at: 2026-07-05T22:00:17.091607+00:00
content_hash: "7e8d85cd3b3853e274fdae60c720e1c86a9093eaa83817b81862f79b019da547"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.25.1 — De-Lattice + enforceable no-stub mode

ruflo 3.25.1 — De-Lattice + enforceable no-stub mode 
 A correctness/honesty patch over 3.25.0. 
 
 De-Lattice the WASM embedder tier. @ruvector/lattice-wasm does not exist (npm 404). The tier is renamed to an honest, opt-in generic WASM-embedder seam : no default package (no 404-by-default), inert unless RUFLO_EMBED_WASM_PKG points it at a real wasm-bindgen embedder. Fail-closed; embeddings resolve to ruvector ONNX exactly as before. 
 Enforceable "no more stubs." RUFLO_REQUIRE_REAL_EMBEDDINGS=1 makes every hash last-resort throw loudly instead of silently returning a semantically-meaningless vector — across neural-tools , vector-db , memory-initializer . Off by default (unchanged degrade behavior). 
 
 Additive · backwards-compatible · fail-closed · zero-regression. npx ruflo@latest . 
 🤖 Generated with RuFlo