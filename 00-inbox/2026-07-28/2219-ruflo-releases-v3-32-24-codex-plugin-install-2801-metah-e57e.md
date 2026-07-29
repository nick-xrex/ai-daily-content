---
id: inbox_51dc6dab
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.24"
author: "ruvnet"
published_at: 2026-07-28T03:59:45+00:00
fetched_at: 2026-07-28T22:19:48.608369+00:00
content_hash: "e57ec167de7fbcd1cd54ef2b4459738eafe257524dce2acc5315181a08a8973b"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.24 — Codex plugin install (#2801) + metaharness hard dependency (ADR-321)

Fixed 
 #2801 — ruflo init --codex/--dual now installs the ruflo-core@ruflo plugin. Before, Codex init set up AGENTS.md, skills, config, and the Ruflo MCP server — but no Ruflo lifecycle hooks. New installRufloCorePlugin() idempotently runs codex plugin marketplace add ruvnet/ruflo --ref main + codex plugin add ruflo-core@ruflo at user scope (canonical upstream plugin, avoiding the #2640 double-firing class), degrades gracefully with a manual-install hint if the Codex CLI is absent, and always emits a prominent ACTION REQUIRED message to trust the hooks in a new Codex session (Codex does not auto-trust command hooks). Ships in @claude-flow/codex@3.0.2 . 
 Changed 
 metaharness promoted to a hard dependency (ADR-321). metaharness@^0.4.1 and @metaharness/router@^0.3.2 moved from optional to dependencies on @claude-flow/cli , so they're always present. ADR-321 supersedes ADR-150's optional-only constraint for these two and records the tradeoff honestly: the MCP metaharness tools invoke via subprocess (zero static imports), so this is functionally a cache-warm for them; the one load-bearing consumer of a declared dep is neural-router.ts 's @metaharness/router import behind CLAUDE_FLOW_ROUTER_NEURAL=1 . Graceful-degradation fallbacks were kept (trivial reversibility). 
 Packages 
 
 
 
 Package 
 Version 
 
 
 
 
 @claude-flow/cli / claude-flow / ruflo 
 3.32.24 
 
 
 @claude-flow/codex 
 3.0.2 
 
 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.24 
 Closes: #2801 . Refs: ADR-321, ADR-150.