---
id: inbox_f1f50d28
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.7.0"
author: "thedotmack"
published_at: 2026-06-20T07:05:05+00:00
fetched_at: 2026-06-20T22:10:33.501825+00:00
content_hash: "06797983121c2480647cae08d7353d8705304d18a938b73cbfff81a6d11c4e81"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.7.0

PostHog telemetry overhaul 
 A ground-up rebuild of claude-mem's telemetry — per-session rollups, unified instrumentation, and real (redacted) error tracking. Grounded in live PostHog data: the raw-event volume was confirmed to be legacy-fleet decay (raw session_compressed fell ~75% in two days as installs updated), so this is the proper rebuild, not a hotfix. 
 What's new 
 
 Per-session rollups — observer_turn_rollup is now emitted once per session at session end ( rollup_reason = session_end | worker_shutdown | safety_flush, plus window_seq ) instead of per 5-minute wall-clock window. Memory-bounded with a safety sweep; drains correctly on worker shutdown. 
 Unified instrumentation — a single instrument() path fans out to the local logger (full fidelity) and telemetry (scrubbed/rolled-up). The logger stays telemetry-free. 
 Redacted error tracking — real error messages + trimmed stacks now reach PostHog as $exception events, consent-gated, profile-less, and fingerprint rate-limited. An allow-then-redact scrubber strips home dirs, absolute paths, DB connection-string credentials, URL userinfo, emails, API tokens (sk-/phc-/ghp-/AWS AKIA/JWT), hex, and IPv4; messages cap at 500 chars, stacks at ~2KB. Autocapture is fully redacted (on-disk source context is stripped, never sent). 
 New kill-switch — CLAUDE_MEM_TELEMETRY_ERRORS=0 disables error capture independently of analytics. 
 Docs — telemetry.mdx rewritten to document the new model, the error-tracking opt-in + one-way-door note, and the opt-out switches. 
 
 Privacy 
 This release begins collecting redacted error messages/stacks (a deliberate, consent-gated shift from whitelist-only telemetry). Raw paths, prompts, project names, source code, and model output are still never collected. Opt out of all telemetry with CLAUDE_MEM_TELEMETRY=0 / DO_NOT_TRACK=1 , or errors-only with CLAUDE_MEM_TELEMETRY_ERRORS=0 . 
 🤖 Generated with Claude Code