---
id: inbox_46087ad9
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.14.2"
author: "ruvnet"
published_at: 2026-06-25T22:07:11+00:00
fetched_at: 2026-06-26T22:23:27.774792+00:00
content_hash: "7d69b53a753c5f8ee36a473facdd4ebef59317d8557857be0162da91cb12be16"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.14.2 — fix Windows embedding crash (#2461)

Patch release fixing a Windows-on-proxy crash and a silent data-loss bug in `memory store`. 
 Fixes 
 
 
 #2461 — `ruflo memory store` / `memory search` crashed with `Cannot read properties of null (reading 'model')` whenever `@xenova/transformers` couldn't fetch model files (corporate proxy, strict firewall, offline). Three independent bugs in the same path: 
 
 `loadEmbeddingModel()` aborted on transformers throw; never reached the working ruvector ONNX fallback that ships in-tree. 
 `generateLocalEmbedding()` then crashed dereferencing the null state. 
 `memory store` without `-n` stored under literal namespace `"undefined"` (silent data loss). 
 
 All three fixed in this release. 
 
 
 Verification 
 
 50× `generateLocalEmbedding` on the published `ruflo@3.14.2` artifact → 50/50 success, 0 crashes 
 100× the same call locally with every embedder module unresolvable → 100/100 success (was: crash on call #1 ) 
 `@claude-flow/cli` builds clean 
 
 Install 
 ```bash 
npx ruflo@3.14.2 
 or 
 npx @claude-flow/cli@3.14.2 
``` 
 All three packages — `@claude-flow/cli`, `claude-flow`, `ruflo` — at 3.14.2 with consistent `latest` / `alpha` / `v3alpha` dist-tags. 
 Credits 
 @Pishro-canadaapply filed #2461 with full root-cause analysis and a proposed fix; this release implements it. 
 PR 
 #2467 — diff and per-commit history.