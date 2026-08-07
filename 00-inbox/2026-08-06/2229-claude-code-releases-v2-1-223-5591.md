---
id: inbox_7ac809d1
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.223"
author: "ashwin-ant"
published_at: 2026-08-06T00:52:37+00:00
fetched_at: 2026-08-06T22:29:12.369941+00:00
content_hash: "559150d5857e375b3c4b136ea80a5bd4bb8e2432f4f8226be9b7286e38fa1659"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.223

What's changed 
 
 Added owner wildcard entries ( "owner/*" ) to the strictKnownMarketplaces and blockedMarketplaces managed settings for allowing or blocking all marketplace repos under a GitHub org 
 Added a warning when workflow agents, forked skills, slash commands, or resumed background agents' requested subagent model is restricted and the parent model runs instead 
 Added a /teleport hint in cloud sessions showing how to continue locally with claude --teleport &lt;session id&gt; 
 Fixed a Bash permission bypass where a crafted command could hide parts of itself from permission checks 
 Fixed permission prompts so commands padded with tabs or invisible Unicode can no longer hide part of the command from the approval dialog 
 Fixed workflow scripts being able to use dynamic import() to run code outside the workflow sandbox 
 Fixed a permission gap where an agent definition's bypassPermissions mode ignored the org bypass-permissions disable policy 
 Fixed resuming a session after a mid-session /cd coming back empty 
 Fixed gateway model discovery hiding Claude models registered under provider-prefixed IDs such as vertex_ai/claude-* or bedrock/anthropic.claude-* 
 Fixed modelOverrides keys that aren't Anthropic model IDs being treated as the session's canonical model ID; unknown keys are now ignored as documented 
 Fixed managed settings: server-delivered settings no longer disable the env block of a machine-local managed-settings.json or MDM profile; admin env now merges per key 
 Fixed sandboxed commands failing to start on Linux when sandbox.filesystem.denyWrite covers the working directory 
 Fixed forked background agents getting stuck "already resuming" for the rest of the session when rebuilding the fork's parent prompt failed during resume 
 Fixed a resumed session failing every turn, or leaving the interactive app on an unresponsive error screen, when its history held a malformed diagnostics attachment 
 Fixed a rare hang when parsing unusual git push output 
 Changed CLAUDE_CODE_DISABLE_1M_CONTEXT to hold every Claude model with a native 1M window to 200K via auto-compaction, not just a fixed list; a startup warning now appears when auto-compaction isn't holding the session to 200K 
 Changed auto-compact to keep sessions on unrecognized model IDs within the assumed context window instead of letting them grow past it; set CLAUDE_CODE_DISABLE_UNKNOWN_MODEL_WINDOW_ENFORCEMENT=1 to restore the previous behavior 
 Changed /review to be an alias of /code-review , which reviews the current diff or a PR ( /code-review &lt;level&gt; &lt;pr#&gt; ); use /code-review ultra for a deep cloud review 
 Changed /code-review with no effort level to reuse the level you typed last; type a level like /code-review high to change it