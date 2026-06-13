---
id: inbox_cd934704
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.6.0"
author: "thedotmack"
published_at: 2026-06-13T01:13:24+00:00
fetched_at: 2026-06-13T03:36:13.640167+00:00
content_hash: "e98d6fef6976a37b9e3c4d3e3f09fa50fb42a9d7335eb8f18c985a51f4d53edc"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.6.0

📊 Historical Telemetry Backfill 
 claude-mem's growth metrics now extend back before telemetry existed. On the first worker start after this upgrade, each install performs a one-time backfill of anonymized daily activity rollups into PostHog via historical-migration ingestion — so installs-over-time, reconstructed WAU/MAU, and cohort retention reflect real usage history instead of starting at the telemetry ship date. 
 What gets sent 
 Anonymous counts only — never titles, prompts, file contents, or project names: 
 
 One profile-less historical_activity event per active day: observation/session/summary/prompt counts, observation-type breakdown, session outcomes, platform buckets, subagent counts, and compression discovery-token totals — all tagged backfilled: true 
 One install_inferred event carrying the install's first active date, drawn from trustworthy session timestamps 
 
 Privacy &amp; safety 
 
 Honors the exact same consent gates as live telemetry: DO_NOT_TRACK , CLAUDE_MEM_TELEMETRY=0 , and telemetry.json opt-out. Opting out before your first post-upgrade worker start prevents the backfill entirely; a later opt-in still backfills. 
 Runs once per install , latched by a completion marker written only after confirmed delivery — failed sends retry on the next worker start, and deterministic event uuids make retries duplicate-safe. 
 CLAUDE_MEM_TELEMETRY_DEBUG=1 dry-runs the full payload to stderr without sending anything. 
 Legacy epoch normalization and corrupt-row guards keep bad timestamps out of the historical record; partial days are never shipped. 
 
 Full disclosure documented at docs.claude-mem.ai/telemetry . 
 PR : #2912