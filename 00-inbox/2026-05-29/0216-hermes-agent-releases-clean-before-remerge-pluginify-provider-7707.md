---
id: inbox_28efdcea
source: hermes-agent-releases
source_type: rss
url: "https://github.com/NousResearch/hermes-agent/releases/tag/clean-before-remerge"
author: "ethernet8023"
published_at: 2026-05-29T13:28:00+00:00
fetched_at: 2026-05-30T02:16:27.715253+00:00
content_hash: "7707fecb0555370232f407b507ed7702274302ee444054fef7a77c5872509cff"
lang: en
caption_quality: None
raw: true
topics: []
---

# clean-before-remerge: Pluginify provider/platform/terminal backends

Move provider adapters (anthropic, bedrock, azure), platform adapters 
(telegram, slack, discord, feishu, dingtalk, matrix), and terminal backends 
(modal, daytona) out of core into plugins/ workspace members. Core references 
them via the plugin registries (get_provider_namespace / get_provider_service / 
get_tool_provider / get_credential_pool_hook) instead of direct imports. 
 
 Provider/platform/terminal adapters relocated under plugins/; pyproject 
extras reference workspace members; nix variants aggregate per-platform extras. 
 Anthropic credential discovery + OAuth-masquerade guard live in the plugin's 
credential_pool_hook; browser-open guarded by _can_open_graphical_browser. 
 Vercel AI Gateway + Vercel Sandbox removed (upstream deletion); get_bedrock_model_ids 
removed (replaced by bedrock_model_ids_or_none + discover_bedrock_models). 
 Terminal backends resolve ModalEnvironment / DaytonaEnvironment lazily from 
the plugin registry. 
 uv.lock regenerated against the pluginified workspace. 
 
 Plugin test suites updated for the relocation: imports point at 
hermes_agent_.adapter, caplog logger-name filters and monkeypatch targets 
use the new module paths, and credential/rollback tests patch 
registries.get_provider_service rather than the removed agent.*_adapter modules. 
 Verified: zero dead imports of relocated modules in core (import smoke test + 
rename-map grep); nix develop succeeds; targeted plugin suites green 
(bedrock, anthropic-auxiliary, matrix, dingtalk, feishu, credential_pool, 
switch_model_rollback). Remaining full-suite failures are pre-existing on the 
pre-merge tree (telegram setUpModule code ) or environmental (voice/media/ 
PTY/network-dependent), not introduced here.