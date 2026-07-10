---
id: inbox_b63fbf52
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.25.6"
author: "ruvnet"
published_at: 2026-07-09T14:19:46+00:00
fetched_at: 2026-07-09T22:09:33.303535+00:00
content_hash: "2dc18cda3e2b28dc596f76f1e142e5043113c7b1462185ded17d675fd8e02230"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.25.6 — main-red unblock + Cursor hook + #2612 heal

Highlights 
 Ships to @claude-flow/cli@3.25.6 , claude-flow@3.25.6 , ruflo@3.25.6 (all three of latest / alpha / v3alpha dist-tags pointed at 3.25.6). 
 Fixes 
 
 #2613 — Cursor's third-party hook import no longer fail-closes every Bash/Edit tool call. ruflo-hook.sh (and its .cjs sibling) now silence CLI stdout, and hooks.json PreToolUse commands emit a valid {"permission":"allow"} verdict that both Claude Code and Cursor accept. 
 #2608 — @claude-flow/plugin-agent-federation shim types synced to agentic-flow@2.0.12-fix.8 ; guard optional close() . Fixes Build V3 red on all 3 platforms. 
 #2608 (extension) — @claude-flow/cli optional-dep imports ( @ruvector/learning-wasm , @ruvector/attention , @metaharness/router ) indirected through string variables so tsc no longer resolves them statically. install-safety builds now compile clean when the optional deps are absent. 
 #2590 — resolved as a consequence of the plugin-agent-federation fix. 
 ADR-150 / #2561 reconciliation — ruflo-metaharness smoke #16 rewritten to enforce the correct ADR-150 rule #2 invariant (no metaharness in ruflo hard dependencies) rather than demanding metaharness presence. Removes the mutual-exclusion with the RUFLO_MAX=0 optional-deps budget guard. 
 #2612 — Duplicate MCP registrations ( claude-flow + ruflo for the same binary) are healed via ruflo doctor detection. The canonical MCP key stays claude-flow to preserve the ~166 plugin tool references to mcp__claude-flow__* ( #2206 ). Doctor now surfaces "Duplicate Ruflo MCP registrations found" with an actionable fix-message pointing operators at the correct entry to remove. 
 
 Release integrity 
 
 Helpers manifest re-signed with Ed25519 for 3.25.6 ; verify-helpers OK. 
 All 726 CLI tests pass locally. 
 CI green on the merged PR (0 failures across 114 checks). 
 
 🤖 Generated with RuFlo