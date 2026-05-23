---
id: inbox_4fddba30
date: 2026-05-16
source_ref: "[[00-inbox/2026-05-16/1800-ruflo-releases-v3-7-0-alpha-44-neural-unblocked-standal-0e94]]"
title: "v3.7.0-alpha.44 — neural unblocked + standalone recipes shipped + npm download badges"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.44
source: ruflo-releases
published_at: 2026-05-16T20:47:36+00:00
fetched_at: 2026-05-22T18:11:11.700407+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo v3.7.0-alpha.44 修復 @claude-flow/neural 導入崩潰與發布管理問題。@ruvector/sona@0.1.6 為空發布（僅含 README + package.json，缺 index.js 與 native bindings），導致 @claude-flow/neural@3.0.0-alpha.8 import 時拋異常；修正至 pin @ruvector/sona@0.1.5（含 index.js + 7 個平台特定 .node 檔）。4 個 standalone modules（memory@3.0.0-alpha.17、embeddings@3.0.0-alpha.18、security@3.0.0-alpha.8、neural@3.0.0-alpha.9）新增 npm/v + npm/dm 下載統計 badge 與 npmjs.com 可見的 standalone recipes，提升 NPM 頁面可信度。Umbrella root README 與 6 個無 badge 模組補充統計，23 個模組中 14 個已有 badge（保持不變）。"
key_points:
  - "@ruvector/sona@0.1.6 空發布導致 @claude-flow/neural@3.0.0-alpha.8 import 崩潰，修正至 pin 0.1.5（含 native bindings）"
  - "4 個 standalone modules 新增 npm 下載統計 badge 與 npmjs.com 可見 recipes（memory、embeddings、security、neural）"
  - "Umbrella root README 與 6 個無 badge 模組補充 npm/v + npm/dm 統計，增進生態可見性"
tags: [package-management, npm-ecosystem, dependency-resolution]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.7.0-alpha.44 — neural unblocked + standalone recipes shipped + npm download badges

RuFlo v3.7.0-alpha.44 修復 @claude-flow/neural 導入崩潰與發布管理問題。@ruvector/sona@0.1.6 為空發布（僅含 README + package.json，缺 index.js 與 native bindings），導致 @claude-flow/neural@3.0.0-alpha.8 import 時拋異常；修正至 pin @ruvector/sona@0.1.5（含 index.js + 7 個平台特定 .node 檔）。4 個 standalone modules（memory@3.0.0-alpha.17、embeddings@3.0.0-alpha.18、security@3.0.0-alpha.8、neural@3.0.0-alpha.9）新增 npm/v + npm/dm 下載統計 badge 與 npmjs.com 可見的 standalone recipes，提升 NPM 頁面可信度。Umbrella root README 與 6 個無 badge 模組補充統計，23 個模組中 14 個已有 badge（保持不變）。

### 重點
- @ruvector/sona@0.1.6 空發布導致 @claude-flow/neural@3.0.0-alpha.8 import 崩潰，修正至 pin 0.1.5（含 native bindings）
- 4 個 standalone modules 新增 npm 下載統計 badge 與 npmjs.com 可見 recipes（memory、embeddings、security、neural）
- Umbrella root README 與 6 個無 badge 模組補充 npm/v + npm/dm 統計，增進生態可見性

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.44)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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

</details>