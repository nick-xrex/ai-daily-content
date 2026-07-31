---
id: inbox_b23e0698
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.33.0"
author: "ruvnet"
published_at: 2026-07-30T19:40:28+00:00
fetched_at: 2026-07-30T22:01:25.226327+00:00
content_hash: "1cf16e319056d10aae3b6e1cb914991612c5c8d1ac7140056f1378c483f79240"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.33.0 — ADR-377: AgentDB Retrieval Security Layer

AgentDB Retrieval Security Layer (ADR-377) 
 Closes #2516 / tracked in #2873 : AgentDB's retrieval and write paths had zero certified defenses against memory poisoning (undefended attack success 93–100% per SMSR, arXiv:2606.12703). Full 3-phase implementation shipped in #2874 , all off by default until independently benchmarked. 
 
 AgentDbRetrievalGuard ( @claude-flow/memory ) — filters HNSW retrieval results through ToolOutputGuardrail 's OWASP LLM01/LLM08 pattern scan before context assembly. CLAUDE_FLOW_RETRIEVAL_GUARD / _STRICT . 
 MemoryPoisonForensics ( @claude-flow/hooks ) — rolling-window z-score anomaly detection on AgentDB write sequences (write-interval, content-length). CLAUDE_FLOW_POISON_FORENSICS=0 to disable. 
 McpCallerIdentity ( @claude-flow/security ) — Ed25519 per-invocation capability tokens. CLAUDE_FLOW_MCP_CALLER_AUTH , off by default pending a follow-on key-distribution ADR. 
 
 Also in this release: 
 
 #2871 — consolidated 49 stale dream-cycle research proposals (open since 2026-05-29, never merged) into ADR-334 through ADR-376, resolving the ADR-147/ADR-179/ADR-320 numbering collisions along the way. 
 #2872 — recovered ADR-377 itself from an abandoned dream-cycle branch that never got a PR opened for it. 
 
 31 new tests across the three touched packages, zero regressions (memory 451, hooks 145, security 570 full suites re-run clean). 
 Packages 
 
 @claude-flow/cli@3.33.0 
 claude-flow@3.33.0 
 ruflo@3.33.0 
 
 🤖 Generated with Claude Code