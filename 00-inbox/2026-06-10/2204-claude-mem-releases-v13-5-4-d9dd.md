---
id: inbox_fa7519ad
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.5.4"
author: "thedotmack"
published_at: 2026-06-10T07:22:17+00:00
fetched_at: 2026-06-10T22:04:26.395798+00:00
content_hash: "d9dd45a158d351fc89c04840efbe08f34c054fccf1d74b81e5017f5295375c4d"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.5.4

Fixed 
 
 Telemetry geolocation: closed the ~98.5% "unknown location" gap. The posthog-node SDK assumes server deployments and stamps $geoip_disable: true on every event by default. claude-mem's worker runs on the user's own machine, so this needlessly suppressed PostHog's ingest-side GeoIP on all worker events ( worker_started , session_compressed , context_injected , ...). The client now passes disableGeoip: false , letting PostHog derive coarse location (country / region / city) at ingestion — from the request IP, which is then discarded. CLI events ( install_* ) were already unaffected. 
 
 Privacy 
 
 No change to the IP promise: raw IP addresses are still never attached to events by the client and never stored — the sender IP is used transiently at ingest for the coarse-location lookup, then discarded. 
 The telemetry docs ( https://docs.claude-mem.ai/telemetry ) and the npx claude-mem telemetry enable consent screen now disclose the ingest-derived coarse location. 
 
 Tests 
 
 New regression test asserts the PostHog client is constructed with disableGeoip: false (telemetry suite now 58 tests, all passing). 
 
 🤖 Generated with Claude Code