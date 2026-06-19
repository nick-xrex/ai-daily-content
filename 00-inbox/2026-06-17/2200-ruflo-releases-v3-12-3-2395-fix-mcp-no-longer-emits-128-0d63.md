---
id: inbox_30d3a210
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.12.3"
author: "ruvnet"
published_at: 2026-06-17T23:38:59+00:00
fetched_at: 2026-06-18T22:00:29.578793+00:00
content_hash: "0d63a59d5d88f8d4433efd101fb058dab7b8171d358f3b6785d85a3e51e32437"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.12.3 — #2395 fix: MCP no longer emits 128-dim mock embeddings

Bundled fix 
 #2395 — MCP memory_store emitted 128-dim mock embeddings (data quality regression) 
 Symptom (per issue): standalone CLI used real 384-dim ONNX embeddings, but the in-session MCP path persistently emitted 128-dim hash-fallback ("mock") embeddings — silently corrupting similarity recall and wasting any benefit of vector memory. 
 Root cause: bridgeGenerateEmbedding returned embedder.embed() results labeled backend: 'onnx' unconditionally, even when AgentDB's vectorBackend controller silently fell back to a 128-dim hash stub. The stub didn't expose isMock=true , so the existing isMock check let it through with a wrong label. 
 Fix: dimensional sanity check. The hardcoded model name Xenova/all-MiniLM-L6-v2 always produces 384-dim; anything else is definitively a stub. Return null from the bridge wrapper in that case so the caller falls through to generateLocalEmbedding , which routes via the real ONNX chain (transformers.js / ruvector). 
 Net: backend labels now match actual semantics, no more silent mock embeddings. 
 Install 
 npx ruflo@3.12.3
 # or 
npm i ruflo@latest 
 All 3 packages × 3 dist-tags published in lockstep. 
 🤖 Generated with RuFlo