---
id: inbox_2bd6438d
source: hermes-agent-releases
source_type: rss
url: "https://github.com/NousResearch/hermes-agent/releases/tag/merge-commit-backup"
author: "ethernet8023"
published_at: 2026-05-28T21:57:55+00:00
fetched_at: 2026-05-30T02:16:27.722889+00:00
content_hash: "b54654dca1337398a04a9a2beb1a43d14d7b336f2a533b2e6d3f1678df3be184"
lang: en
caption_quality: None
raw: true
topics: []
---

# merge-commit-backup: Merge origin/main into ethie/oh-god (pluginify refactor reconciliation)

Reconciles the "pluginify everything" refactor (moving provider adapters, 
platform adapters, and terminal backends out of core into plugins/) with 
267 commits of main. main had 515 edits across 635 files; our branch moved 
98 files into plugins/. The dangerous class was main editing files at OLD 
paths that we relocated — handled below. 
 STRUCTURAL DECISIONS 
 
 ai-gateway + vercel_sandbox: honored main's PR #33067 deletion. Dropped our 
orphaned plugins/terminals/vercel/ dir and all 3 stale vercel refs that 
survived in pyproject (workspace member, [all] entry, uv source). 
 tools/lazy_deps.py: kept main's version. Our branch deleted it incompletely 
(WIP) while main has 30 live callers + active maintenance. main's intent won. 
 agent/agent_runtime_helpers.py: COMBINED — main's atomic swap+rollback 
snapshot envelope wraps our pluginified registries-based anthropic imports. 
 agent/credential_pool.py: took our plugin-hook indirection AND ported main's 
api_key_path_explicit OAuth-masquerade security fix INTO the anthropic 
credential_pool_hook (it was pluginified from a pre-fix base and would have 
been silently dropped otherwise). 
 hermes_cli/model_switch.py, hermes_cli/models.py: took main's logic 
(cached_provider_model_ids, AI-gateway removal) then re-applied our pluginify 
import rewrites (agent.bedrock_adapter/anthropic_adapter -&gt; registries 
namespace lookups) since those modules moved to plugins. 
 tools/terminal_tool.py: took main's version (vercel_sandbox deletion) then 
restored our lazy registry resolution for modal + daytona environments 
(both moved to plugins; main's direct imports would crash at runtime). 
 nix/checks.nix: kept both — our hermetic-boundary checks + main's 
messaging-variant discord.py guard. 
 pyproject.toml: plugin extras as workspace members (ours) + main's new wecom 
extra; vercel removed throughout. 
 uv.lock: regenerated with uv lock (not hand-merged); 233 packages. 
 
 VERIFICATION 
 
 Zero conflict markers anywhere. 
 Exhaustive 17-moved-module grep: no dead imports of relocated modules in core. 
 Import smoke test: all hot core modules import clean. 
 Targeted tests (21 files incl. credential_pool, anthropic plugin, 
run_agent, project_metadata): pass. 
 3 credential_pool security tests rewired to register the real plugin hook 
(core tests don't trigger plugin discovery): pass. 
 Full suite: remaining failures are pre-existing on premerge-oh-god (telegram 
collection error: setUpModule MagicMock code ) or environmental (matrix 
DNS/e2ee-deps, network) — NOT introduced by this merge. See PR notes.