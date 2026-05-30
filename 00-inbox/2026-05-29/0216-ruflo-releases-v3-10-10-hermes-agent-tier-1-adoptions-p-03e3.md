---
id: inbox_7ea00382
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.10"
author: "ruvnet"
published_at: 2026-05-29T18:59:04+00:00
fetched_at: 2026-05-30T02:16:29.844992+00:00
content_hash: "03e3b9670ae453607d01e69f2a8aec75f36fd5d1ae0f64870fd2129e712f8efd"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.10 — Hermes-Agent Tier-1 adoptions (prompt caching, reasoning scrub, tool-loop breaker)

Ruflo v3.10.10 — Hermes-Agent Tier-1 adoptions 
 The 3 small, high-confidence, in-repo patterns worth borrowing from NousResearch/Hermes-Agent , from a deep-research capability map (the rest were SKIP or ADR-gated; the map also produced 5 corrections to ADR-113/ #1907 ). 
 
 Prompt caching — agent_execute 's direct Anthropic call now marks the system prompt as an ephemeral cache breakpoint (~90% discount on cached input tokens, 5-min TTL). Same strategy applied to @claude-flow/providers (gated by config.promptCache , default on). 
 Reasoning-tag scrub — trajectory action/result are stripped of &lt;think&gt; / &lt;thinking&gt; / &lt;reasoning&gt; / &lt;REASONING_SCRATCHPAD&gt; blocks before DISTILL, so extended-thinking tokens don't contaminate the pattern embeddings the learning loop relies on. Boundary-gated. 
 Tool-loop circuit breaker — pre-command warns at 3 / blocks at 5 consecutive failures of the same command (with a recovery hint), fed by post-command . Orthogonal to the injection-focused security guardrail; advisory by default. 
 
 Honest note: @claude-flow/providers is not consumed by the cli, so the cli-effective prompt-caching fix is in agent-execute-core.ts ; the providers change ships on its own cadence. 
 CI 29/29 green; all three packages at 3.10.10 (latest/alpha/v3alpha lockstep). 
 🤖 Generated with RuFlo