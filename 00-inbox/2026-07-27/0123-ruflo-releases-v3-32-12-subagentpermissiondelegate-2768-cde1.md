---
id: inbox_d32d9d7c
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.12"
author: "ruvnet"
published_at: 2026-07-27T00:22:28+00:00
fetched_at: 2026-07-27T01:23:04.178153+00:00
content_hash: "cde1975227d495769b36da18c3de061ce9b3b3e278bf60d45b5a9c3a89c3d69d"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.12 — SubagentPermissionDelegate (#2768) + Flash Attention credibility cleanup (#2739 dream)

Two dream-cycle items shipped together. 
 Fixed / Added 
 
 
 #2768 SubagentPermissionDelegate — new swarm init --with-permissions &lt;preset&gt; flag ships a per-role capability manifest to .swarm/permissions.jsonl and seeds an append-only audit trail at .swarm/permission-audit.jsonl . Presets: strict , standard , permissive . Metadata + audit layer only — Claude Code's Task tool owns runtime enforcement. E2E verified in a fresh scratch cwd: 3 role rows + 3 granted events written, state.json records the preset, bogus presets fail cleanly at parse time. Closes the ClawArena "privilege-granting is #1 orchestration bottleneck" gap from arXiv 2606.31174. 
 
 
 #2739 Flash Attention credibility cleanup — dropped the "2.49x-7.47x speedup" claim from all 5 CLAUDE.md sites. It was inherited from upstream marketing and never reproduced in-tree. Every dream-cycle for 7+ nights flagged it as a credibility drag. Doc now reads "integration available; measured speedup pending benchmark" and explains WHY the number was dropped. 
 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.12 
 Refs: dream-cycles #2727 #2739 #2752 #2760 #2763 #2768 #2778 #2783 (Flash Attention flagged repeatedly), #2768 (ClawArena).