---
id: inbox_40bb3859
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.15"
author: "ruvnet"
published_at: 2026-07-27T02:29:25+00:00
fetched_at: 2026-07-27T22:45:54.321575+00:00
content_hash: "4859e1e4b4ddb25679bbe2bde45699c702040d03a2f9f5fe342a84171ea8d0f0"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.15 — MCP Composition Inspector (#2783 dream — cross-tool prompt-injection scan)

First dream-cycle backlog item shipped after the parser scoping fix. 
 Added 
 ruflo security composition-scan — deterministic (no LLM) scanner that reads a set of MCP tool descriptors and flags three attack signatures targeting the ShareLock Shamir-split prompt-injection pattern (arXiv 2606.27027, dream-cycle #2783 ): 
 
 Injection-phrase — 16 known prompt-injection phrases inside a single tool. 
 Shared-fragment — identical substrings ≥ N chars across tool descriptions, capped at ≤ K distinct tools per fragment. Attack fragments live in small conspiracies (2-3 tools); template language shows up in dozens. 
 Name-lookalike — tool names ≤ 2 edits from a trusted ruflo prefix (typosquat mitigation). 
 
 Usage: 
 ruflo security composition-scan # scan the CLI's own MCP tools
ruflo security composition-scan --tools-json X.json # scan a third-party MCP registry
ruflo security composition-scan --min-fragment 30 --top 50
 
 Verification 
 
 Unit tests: 6/6 pass (shared-fragment, injection-phrase, name-lookalike, ruflo-benign-baseline, stats accuracy, minFragment tuning). 
 E2E on synthetic malicious 4-tool registry: all 3 signatures flagged correctly. 
 E2E on the CLI's own 350-tool registry: population cap knocks false-positives 92× (152,560 → 1,788). 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.15 
 Refs: dream-cycle #2783 (2026-07-26).