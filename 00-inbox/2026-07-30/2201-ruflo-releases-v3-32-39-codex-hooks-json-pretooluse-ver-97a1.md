---
id: inbox_1b71f78e
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.39"
author: "ruvnet"
published_at: 2026-07-30T02:12:29+00:00
fetched_at: 2026-07-30T22:01:25.236466+00:00
content_hash: "97a1ff93982e2fe31ba8cb1cf1bbd299818f7adbd1f6f94fa2c6818dde578e24"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.39 — Codex hooks.json + PreToolUse verdict compat

Fixes 
 #2855 — Codex's plugin hook-manifest loader accepts only description and hooks at the top level. plugins/ruflo-core/hooks/hooks.json and plugins/ruflo-cost-tracker/hooks/hooks.json carried _note / _platform_note documentation fields, so a fresh Codex install of ruflo-core@ruflo failed to load the plugin at all with unknown field \ _note`, expected `description` or `hooks` . Fixed by folding the doc content into description . Added a permanent CI guard ( scripts/audit-plugin-hooks-cross-platform.mjs`) so this can't regress silently again. 
 #2856 — Once the manifest could load, modify-bash / modify-file PreToolUse hooks always echoed Cursor's {"permission":"allow"} verdict, which Codex's own stricter output schema rejects outright ( hook returned invalid pre-tool-use JSON output ) — verified directly against the real parser ( codex-rs/hooks/src/engine/output_parser.rs ). Hardened Codex-host detection with a turn_id -based fallback alongside the existing PLUGIN_ROOT / PLUGIN_DATA env-var check. 
 ruflo-core bumped 0.2.5 → 0.2.6 and ruflo-cost-tracker 0.26.2 → 0.26.3 so Codex's per-version plugin cache invalidates and picks up the fix rather than serving a stale cached copy indefinitely. 
 PR: #2857 
 Packages 
 `@claude-flow/cli`, `claude-flow`, and `ruflo` are all at 3.32.39 ; `latest`, `alpha`, and `v3alpha` dist-tags all point to it.