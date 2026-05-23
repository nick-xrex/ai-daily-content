---
id: inbox_903cb64b
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.23"
author: "ruvnet"
published_at: 2026-05-11T13:14:03+00:00
fetched_at: 2026-05-22T18:00:34.021779+00:00
content_hash: "6bae72753724ec84ceaaf769b8632d99721bed0a5fc95f0dbfd327794cdbba62"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.7.0-alpha.23 — task-status crash fix

Patch release — bug fixes 
 #1863 — task status no longer crashes 
 task status &lt;id&gt; threw TypeError: Cannot read properties of undefined (reading 'join') when a task had no dependencies/dependents/tags (created via task create , or loaded from an older store schema). The command formatter assumed those fields were always arrays; the MCP server legitimately omits them. Now guarded with ?.join() || 'None' at all five sites. 
 Also added a cli-no-crash CI smoke ( task create → task status + task list / agent list / memory list / swarm status ) that fails the build on any unhandled-exception crash — so this class doesn't recur. 
 #1899 — ruflo-core hooks call the right package 
 The ruflo-core plugin's hooks.json referenced npx claude-flow@alpha in all 5 hook commands, causing ETIMEDOUT errors on every session-end during brief network blips. Now uses npx ruflo@alpha . Note: the marketplace plugin distributes via IPFS — update ruflo-core ( /plugin update ruflo-core ) once ruflo-core@0.2.2 is republished to get this. The npm-CLI side is fixed in this release. 
 Still open / explained 
 
 #1863 (execution half) — task assign → autonomous daemon pickup → execution is the part not wired end-to-end yet (ADR-095 G1). The crash is fixed; the daemon worker-pool wire is the remaining tracker. The working path today is agent_spawn → agent_execute (the latter calls the Anthropic API). 
 Branding sweep ( #1858 , #1861 ) — display strings still say claude-flow in a few places (MCP server key in .mcp.json , doctor banner, daemon log). Batched for an upcoming alpha. Package names like @claude-flow/aidefence stay — they're the actual published packages. 
 
 Install 
 npx ruflo@latest # → 3.7.0-alpha.23 
npx claude-flow@latest # → 3.7.0-alpha.23