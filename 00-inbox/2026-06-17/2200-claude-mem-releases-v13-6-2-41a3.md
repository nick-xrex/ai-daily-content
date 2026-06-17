---
id: inbox_d6321dd0
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.6.2"
author: "thedotmack"
published_at: 2026-06-17T20:24:06+00:00
fetched_at: 2026-06-17T22:00:27.415278+00:00
content_hash: "41a3f2c3c36b0a11b298a9e164381e254421826970324885bcc2b4f4f03fde24"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.6.2

What's Changed 
 Telemetry cost reduction ( #2977 ) 
 
 TelemetryBuffer rollup windows — high-volume session_compressed and context_injected events are now aggregated into 5-minute rollup windows ( observer_turn_rollup , context_injected_rollup ) before forwarding to PostHog, replacing ~45M individual events/month with ~20K rollup records. Cuts the projected PostHog bill from ~$7,700/mo to ~$10/mo without losing aggregate shape (counts, sums, averages, top model, per-outcome buckets). 
 Outcome visibility in context_injected_rollup — added outcomes_ok / outcomes_error buckets so a window of 100% failed injections is distinguishable from one of zero-token successes. 
 
 CI 
 
 Windows build pinned to windows-2022 — the windows-latest image moved to windows-2025 (Visual Studio 18), which the bundled node-gyp@11.5.0 can't detect, breaking native tree-sitter rebuilds. Pinned to windows-2022 (VS2022) until node-gyp gains VS18 support. 
 
 Full Changelog : v13.6.1...v13.6.2