---
id: inbox_dda9babc
date: 2026-06-09
source_ref: "[[00-inbox/2026-06-09/2200-ruflo-releases-v3-10-40-community-merges-model-router-d-4fb8]]"
title: "v3.10.40 — community merges (model-router docs, statusline, typo) + drift-guard regen"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.40
source: ruflo-releases
published_at: 2026-06-09T12:43:59+00:00
fetched_at: 2026-06-09T22:06:26.794689+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.40 補丁版本整合四項社區貢獻與一次 drift-guard 重新生成。首先同步 model-router 文檔，釐清採用的是 Thompson Beta-Bernoulli bandit 架構而非 FastGRNN；其次修復 statusline 版本探測，解決自定義 npm prefix（~/.npm-global）無法偵測導致版本誤判為 3.6，並新增本地 sqlite3 查詢支援使 AgentDB/Tests/Hooks/Integration 段正確顯示；三是修正 typo；四是修正 MCP 權限規則 mcp__claude-flow__:* → mcp__claude-flow__*。所有合併項目均經過安全審計，無網路外洩、密鑰洩露或注入風險。"
key_points:
  - "model-router 文檔同步：採用 Thompson Beta-Bernoulli bandit 架構，而非 FastGRNN（#2330）"
  - "statusline 修復：npm 自定義前綴探測（npm_config_prefix、PREFIX、~/.npm-global），本地 sqlite3 overlay 正確計算 AgentDB/Tests/Hooks/Integration 段（#2331）"
  - "MCP 權限規則修正及 typo 修正：mcp__claude-flow__:* 移除冒號使規則有效、3 個 README 中 ruvflo → ruflo（#2306、#2328）"
tags: [ruflo, claude-flow, statusline, npm, security]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.40 — community merges (model-router docs, statusline, typo) + drift-guard regen

Ruflo v3.10.40 補丁版本整合四項社區貢獻與一次 drift-guard 重新生成。首先同步 model-router 文檔，釐清採用的是 Thompson Beta-Bernoulli bandit 架構而非 FastGRNN；其次修復 statusline 版本探測，解決自定義 npm prefix（~/.npm-global）無法偵測導致版本誤判為 3.6，並新增本地 sqlite3 查詢支援使 AgentDB/Tests/Hooks/Integration 段正確顯示；三是修正 typo；四是修正 MCP 權限規則 mcp__claude-flow__:* → mcp__claude-flow__*。所有合併項目均經過安全審計，無網路外洩、密鑰洩露或注入風險。

### 重點
- model-router 文檔同步：採用 Thompson Beta-Bernoulli bandit 架構，而非 FastGRNN（#2330）
- statusline 修復：npm 自定義前綴探測（npm_config_prefix、PREFIX、~/.npm-global），本地 sqlite3 overlay 正確計算 AgentDB/Tests/Hooks/Integration 段（#2331）
- MCP 權限規則修正及 typo 修正：mcp__claude-flow__:* 移除冒號使規則有效、3 個 README 中 ruvflo → ruflo（#2306、#2328）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.40)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release rolling up four community merges and one drift-guard regen. 
 Merged 
 
 #2330 — docs(router): make model-router docs match shipped impl (Option A for #2329) — reconciles model-router.ts header, ADR-026, and the hooks-tools.ts implementation tag with the actually-shipped router (lexical complexity heuristic + Thompson Beta-Bernoulli bandit, not the FastGRNN/Tiny-Dancer neural design @rcraw flagged). Private member tinyDancerRouter → baseRouter in EnhancedModelRouter ; public getStats() field kept as tinyDancerStats for telemetry-schema stability. Option B (real @ruvector/tiny-dancer wiring) deferred until a trained FastGRNN safetensors artifact exists. 
 #2331 — fix(statusline): resolve version for custom npm prefix + populate AgentDB/Tests/Hooks/Integration segments ( @Tomi2k ). Two real bugs:
 
 Custom npm prefix ( ~/.npm-global ) probe was missing → version fell back to hard-coded '3.6' . Now probes npm_config_prefix , PREFIX , and the common ~/.npm-global default alongside the binDir-relative paths. 
 AgentDB / Tests / Hooks / Integration segments rendered permanent 0 / none because hooks statusline --json only returns user/v3Progress/security/swarm/system . Adds 4 local-overlay helpers ( getLocalAgentDB , getLocalTests , getLocalHooks , getLocalIntegration ) wired through applyLocalOverlays() . Read-only sqlite3 query ( mode=ro ), bounded depth-4 directory walk, all catches degrade to zeros. 
 
 
 #2328 — docs: fix typo 'ruvflo' -&gt; 'ruflo' in install instructions ( @antonbozko-cell ). Trivial 3-character fix across 3 READMEs. 
 #2306 — fix(init): correct MCP allow rule mcp__claude-flow__:* -&gt; mcp__claude-flow__* ( @S23Web3 ). Removed a stray colon that made the permission rule invalid. (Already merged yesterday; included here for changelog completeness.) 
 
 Closed (duplicate) 
 
 PR #2325 ( @mamd69 ) — also proposed a fix for #2302 but with mcp__ruflo__* , which would silently break MCP permissions because the server is registered as claude-flow (see v3/@claude-flow/cli/src/init/mcp-generator.ts:113-130 ). Closed with thanks; #2306 already shipped the correct fix. 
 
 Drift-guard regen 
 Committed .claude/helpers/statusline.cjs snapshot was stale relative to #2331 's generator changes — regenerated, statusline-cost-display.test.ts drift guard passes 8/8. 
 Packages 
 
 
 
 Package 
 Old 
 New 
 Tags 
 
 
 
 
 @claude-flow/cli 
 3.10.39 
 3.10.40 
 latest, alpha, v3alpha 
 
 
 claude-flow 
 3.10.39 
 3.10.40 
 latest, alpha, v3alpha 
 
 
 ruflo 
 3.10.39 
 3.10.40 
 latest, alpha, v3alpha 
 
 
 @claude-flow/memory 
 3.0.0-alpha.20 (unchanged) 
 — 
 — 
 
 
 
 Security review 
 All four merged PRs were diff-audited before merge: no network exfil, no secret reads, no eval/Function/child_process surprises, no postinstall hooks, no obfuscation, no dependency additions. #2331 's new sqlite3 invocation uses mode=ro with statically-formed SQL (no injection vector) and is wrapped in a degrade-to-zero catch.

</details>