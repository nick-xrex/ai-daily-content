---
id: inbox_4b6424fd
source: superpowers-releases
source_type: rss
url: "https://github.com/obra/superpowers/releases/tag/v6.1.0"
author: "obra"
published_at: 2026-06-30T18:42:18+00:00
fetched_at: 2026-07-01T23:31:25.564901+00:00
content_hash: "0bf96f4f6927cc1690dfe402baa9e9be129d9015696cdf801f682599c8443a2e"
lang: en
caption_quality: None
raw: true
topics: []
---

# v6.1.0

Lower Per-Session Token Cost 
 The using-superpowers bootstrap is injected into every session, so its size is paid for constantly. This release trims it and the per-harness references it points to, without dropping behavior-shaping content. 
 
 Compressed the using-superpowers bootstrap. Replaced the graphviz skill-flow diagram with the prose it encoded, folded the standalone Instruction-Priority section into User Instructions, dropped the per-platform "How to Access Skills" walkthrough, and trimmed the Platform Adaptation pointer to the harnesses that still ship a reference file. The full Red Flags rationalization table and the user-instruction precedence rules are unchanged. 
 Pruned the per-harness tool-mapping references. The verbose action-to-tool tables restated guidance modern agents already follow. Each reference file is trimmed to the harness-specific notes that still carry weight — subagent dispatch, task tracking, instructions-file paths — and claude-code-tools.md and copilot-tools.md , which had nothing harness-specific left, are deleted. 
 
 Codex 
 
 Codex can install from the marketplace. Codex marketplace sources expect a .agents/plugins/marketplace.json at the marketplace root; the repo only shipped the Claude marketplace file, so Codex could name the marketplace but found no installable plugin entries. A repo-local Codex marketplace manifest now points at the same repository root, so the plugin is installable from Codex. 
 Codex no longer ships a SessionStart hook. Codex reliably triggers skills on its own, and the bootstrap hook made the UX worse rather than better. The Codex hook config ( hooks-codex.json ) and its manifest registration are removed. 
 
 Harness Support 
 
 Gemini CLI support removed. Google EOLed the Gemini CLI on 2026-06-18; the extension can no longer be installed or updated. Gemini is gone from the install docs, the subagent-capable platform lists, and the eval-harness description, and its tool-mapping reference is deleted.