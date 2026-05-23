---
id: inbox_4fddba30
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.44"
author: "ruvnet"
published_at: 2026-05-16T20:47:36+00:00
fetched_at: 2026-05-22T18:00:34.014241+00:00
content_hash: "0e94252d850403863b03d1d12e965096e1cff15c0f239ef8add677fbd7b959d6"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.7.0-alpha.44 — neural unblocked + standalone recipes shipped + npm download badges

Closes the chain from ca0a6fa5c (standalone recipes landed in repo but never reached npm). Three threads converge here: 
 1. @claude-flow/neural unblocked ( #2022 ) 
 @claude-flow/neural@3.0.0-alpha.8 pinned \"@ruvector/sona\": \"latest\" , and @ruvector/sona@0.1.6 shipped as an empty publish (README + package.json only — no index.js , no native bins). Every fresh npm install @claude-flow/neural broke at import time. 
 Fix: @claude-flow/neural@3.0.0-alpha.9 pins to the exact known-good @ruvector/sona@0.1.5 (which has index.js + 7 platform-specific .node files). Tracking issue #2022 for the upstream sona republish. 
 Post-publish live check (the bug shape): 
``` 
$ npm install @claude-flow/neural@3.0.0-alpha.9 
$ node -e "import('@claude-flow/neural').then(m =&gt; console.log(Object.keys(m).slice(0,5)))" 
[A2CAlgorithm, BalancedMode, BaseModeImplementation, BatchMode, CuriosityModule] 
``` 
 2. Standalone recipes now visible on npmjs.com 
 The standalone-use sections added in ca0a6fa5c lived only in the repo READMEs. This release bumps and republishes the four modules so npmjs.com finally shows the recipes that prove these packages work without the CLI: 
 
 
 
 Package 
 Version 
 What's new on npmjs.com 
 
 
 
 
 @claude-flow/memory 
 3.0.0-alpha.17 
 HNSW + Registry-with-injected-AgentDB recipes 
 
 
 @claude-flow/embeddings 
 3.0.0-alpha.18 
 MockEmbeddingService + cosineSimilarity recipe 
 
 
 @claude-flow/security 
 3.0.0-alpha.8 
 InputValidator + PasswordHasher + CredentialGenerator + SafeExecutor + PathValidator recipes 
 
 
 @claude-flow/neural 
 3.0.0-alpha.9 
 MoE Router standalone recipe 
 
 
 
 3. npm download badges across the README surface 
 Every published package README now carries npm/v + npm/dm badges so live download volume is visible. Added to: 
 
 Umbrella root README.md (badges for both ruflo + claude-flow ) 
 6 modules that had no npm badges at all ( claims , cli-core , plugins , plugin-agent-federation , plugin-iot-cognitum , and cli itself via the root README) 
 3 modules with version-only badges ( browser , codex , mcp ) 
 14 modules already had both — left untouched 
 
 The ruflo/README.md and v3/@claude-flow/cli/README.md auto-copy from root via prepublishOnly , so they inherit the new badge bar. 
 Versions 
 
 
 
 Package 
 Version 
 Tag(s) 
 
 
 
 
 @claude-flow/memory 
 3.0.0-alpha.17 
 latest, alpha, v3alpha 
 
 
 @claude-flow/embeddings 
 3.0.0-alpha.18 
 latest, alpha, v3alpha 
 
 
 @claude-flow/security 
 3.0.0-alpha.8 
 latest, alpha, v3alpha 
 
 
 @claude-flow/neural 
 3.0.0-alpha.9 
 latest, alpha, v3alpha 
 
 
 @claude-flow/cli 
 3.7.0-alpha.44 
 latest, alpha, v3alpha 
 
 
 claude-flow 
 3.7.0-alpha.44 
 latest, alpha, v3alpha 
 
 
 ruflo 
 3.7.0-alpha.44 
 latest, alpha, v3alpha 
 
 
 
 Install 
 ```bash 
npx ruflo@latest 
 or 
 npx @claude-flow/cli@latest doctor 
``` 
 Commit: 5b71c7ac1 
 🤖 Generated with RuFlo