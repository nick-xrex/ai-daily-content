---
id: inbox_c96d3c41
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.5.1"
author: "thedotmack"
published_at: 2026-06-10T04:43:24+00:00
fetched_at: 2026-06-10T22:04:26.421196+00:00
content_hash: "4456276126123e5a49527bd13c6f0211aac94d64200cf8aac8763f7b06b4afe0"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.5.1

What's New in 13.5.1 
 Deep telemetry instrumentation (anonymous, opt-out — see npx claude-mem telemetry ): 
 
 context_injected now reports token economics and observation-type breakdowns via the new generateContextWithStats() context builder, so we can measure real context savings. 
 session_compressed enriched with provider, model, real per-call token counts (Claude, Gemini, and OpenRouter at parity), latency, and observation-type breakdown. 
 Lifecycle events now create person profiles with IDE, provider, and mode properties, unlocking retention/cohort analytics (DAU/WAU via daily worker heartbeat). 
 worker_started capture moved after DB init so it reflects a genuinely live worker. 
 Telemetry scrub whitelist expanded and tested for all new properties; consent screen and docs list every property collected. 
 
 🤖 Generated with Claude Code