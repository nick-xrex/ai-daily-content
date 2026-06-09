---
id: inbox_dda9babc
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.40"
author: "ruvnet"
published_at: 2026-06-09T12:43:59+00:00
fetched_at: 2026-06-09T22:00:29.569389+00:00
content_hash: "4fb8af2e512aa5b3a7b09979e5970fbabbd7ea091708eb4f828ea6f7dae9a4ee"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.40 — community merges (model-router docs, statusline, typo) + drift-guard regen

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