---
id: inbox_c33e9ec2
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.5.3"
author: "thedotmack"
published_at: 2026-06-10T06:09:24+00:00
fetched_at: 2026-06-10T22:04:26.398570+00:00
content_hash: "9b82c31a81d558eee548c2c362fadf9e6af52a61df801dbad6d03cec587079b2"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.5.3

Telemetry: real data edition 
 Every analytics number claude-mem reports about itself is now real, provider-reported data — plus a new daily install-state snapshot so we can see the actual state of the installed base. 
 Fixed: the four session_compressed data-quality bugs 
 
 Claude token counts were placeholders. The Agent SDK attaches an early-streaming usage snapshot to assistant messages ( output_tokens of ~2–10, regardless of actual output). The session_compressed event is now fired from the SDK result message, which carries the finalized per-turn usage — verified empirically (placeholder said 8, result said 45). Compression ratios for Claude models drop from a nonsensical 6,000–38,000 to the true ~10–100 range. 
 cost_usd is now real and populated. Claude: computed from the SDK's cumulative total_cost_usd delta between consecutive turns. OpenRouter: usage.cost + cost_details.upstream_inference_cost (covers BYOK), with usage accounting requested from openrouter.ai only. Gemini reports no cost, so the field stays honestly absent — never estimated. 
 Impossible compression ratios (&lt; 1, or exactly 0.0) eliminated. Custom OpenAI-compatible gateways that report suffix-only or one-sided token usage can no longer produce half-real events: usage is now both-sides-or-nothing, ratios require input &gt; 0, and a new endpoint_class property ( openrouter | custom ) lets dashboards segment gateway-reported data. 
 model is never silently missing or wrong. The model that actually served the request ( response.model ) is stamped instead of the raw configured string, array-typed model settings are normalized, error-path events now carry the model, and unknown is the floor everywhere — non-string values previously vanished in the telemetry scrubber. 
 
 New: install-state snapshot 
 worker_started (start + daily heartbeat) now reports an aggregate snapshot of the local memory DB as person properties: observation/session/summary/project counts, DB file size, install age in days, observations in the last 7/30 days, and days since the last observation. Counts and day-deltas only — never project names, text, or any content. Makes retention, scale, and activity cohorts directly sliceable in analytics. 
 Also fixed 
 
 The ide person property on worker_started never populated — the lookup queried a legacy table and silently threw on every start since it shipped. 
 Epoch math now normalizes legacy seconds-unit rows (a few hundred per install) that would have reported install ages of ~20,000 days. 
 
 All new properties are whitelisted in the scrubber, documented at https://docs.claude-mem.ai/telemetry , and shown in the npx claude-mem telemetry consent screen. Telemetry remains anonymous and opt-out ( npx claude-mem telemetry disable ). 
 🤖 Generated with Claude Code