---
id: inbox_105a0401
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.5.5"
author: "thedotmack"
published_at: 2026-06-10T09:53:56+00:00
fetched_at: 2026-06-10T22:04:26.389151+00:00
content_hash: "d4c084b3acb1c94996b8386427315eb02318eba56831704d305f3d97c2bab305"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.5.5

Telemetry Reliability Signals (Plan 14) 
 claude-mem instrumented success well — failure was invisible. This release adds the five highest-value missing reliability signals ( #2874 ). Everything is closed-enum/count-only, whitelisted in the scrubber, and disclosed in both the public docs and claude-mem telemetry . 
 Search retrieval quality ( search_performed ) 
 
 result_count , search_strategy ( chroma|fts|filter_only ), chroma_available , fallback_reason ( none|chroma_connection|chroma_error|chroma_not_initialized ) 
 Zero-result rate is now computable, and Chroma's silent degradation to FTS is visible. 
 
 Compression trust ( session_compressed ) 
 
 fabrication_detected / fabricated_count — commit-hash fabrication by the observer model, on every emit path 
 Respawn-gated invalid-output events: invalid_output_class ( xml|idle|prose|poisoned ), consecutive_invalid_outputs , respawn_triggered 
 outcome: aborted with abort_reason ( idle|shutdown|overflow|restart_guard|quota|poisoned|none ), emitted where all abort flows converge 
 
 Worker lifecycle 
 
 New worker_stopped event: uptime_seconds , shutdown_reason ( stop|restart|signal ) 
 Crash detection via clean-shutdown sentinel: worker_started now reports previous_shutdown ( crash|clean|unknown ) and previous_uptime_seconds 
 Memory health: integer process_rss_mb / heap_used_mb on lifecycle events and the heartbeat 
 
 Hook failures 
 
 New hook_failed event over the direct CLI transport (the worker being unreachable IS the failure being reported), threshold-gated on the fail-loud counter and awaited before process exit so events survive short-lived hook processes 
 
 Fixes 
 
 CI : the PostHog disableGeoip regression test was order-dependent and failed full-suite runs (CI on main had been red since v13.5.4). posthog-node is now mocked globally via a bun test preload — which also guarantees test runs can never construct a real PostHog client and flush fabricated events into production analytics. 
 Windows-managed shutdown IPC now forwards the restart reason for shutdown_reason fidelity.