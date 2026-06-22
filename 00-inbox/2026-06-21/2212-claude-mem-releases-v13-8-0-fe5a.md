---
id: inbox_3f9049c3
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.8.0"
author: "thedotmack"
published_at: 2026-06-21T20:33:47+00:00
fetched_at: 2026-06-21T22:12:57.822315+00:00
content_hash: "fe5a161b8f60a8b1b8b7bd6f2aae393497e9a63bbc4bb83459617a85b51a6a5a"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.8.0

Telemetry: observation volume on per-session rollups 
 Carries generation-side observation volume and type mix on the observer_turn_rollup event so cache-value KPIs survive the migration off the legacy per-occurrence session_compressed / context_injected streams. 
 What's new 
 
 observer_turn_rollup now sums observations_created and the obs_type_* family (bugfix / discovery / decision / refactor / other) across every compression turn in a session. Paired with total_cost_usd , this makes cost-per-observation and observation-type-by-model derivable from the rollup alone. 
 context_injected_rollup carries total_observations_injected and total_tokens_saved_vs_naive — context-cache value (observations served × cost/obs) is now derivable from the rollup. 
 scrub.ts whitelist extended for the new aggregate keys; all values are counts/sums only — never names, prompt text, or raw strings. 
 Public telemetry.mdx docs updated to document the new rollup fields. 
 
 Merge notes 
 
 Merged latest main (Ponytail audit, v13.7.1), which removed fabrication tracking; the now-stale fabrication_count / fabricated_count references were dropped from code and docs accordingly. 
 
 Full changes: #3017