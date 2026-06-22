---
id: inbox_6b4c4417
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.7.1"
author: "thedotmack"
published_at: 2026-06-21T20:16:23+00:00
fetched_at: 2026-06-21T22:12:57.837954+00:00
content_hash: "c106d2fb685b35e6d4f7d8ea95a8da9b7a37746f5c1ad3291781896320e6d241"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.7.1

Cleanup + reliability release. No new user-facing features. 
 Fixed 
 
 Node version floor corrected. engines.node now requires &gt;=20.12.0 to match the stdlib util.parseEnv adopted during the audit. It previously advertised &gt;=20.0.0 , where util.parseEnv is undefined — causing silent credential-load failures (and a hard throw in saveClaudeMemEnv ) on Node 20.0–20.11. Fixed in both the npm package and the generated plugin manifest. ( #3021 ) 
 
 Changed (internal) 
 
 Ponytail audit — −10.4k lines of dead/redundant code removed across 8 slices (worker HTTP routes, agents, session/rate-limit, search pipeline, providers, storage/shared). 
 Provider refactor. New OpenAICompatibleProvider base class unifies the Gemini and OpenRouter session lifecycle; per-provider behavior preserved via abstract flags ( requireNonEmptyToTruncate , forwardEmptyMessageResponse ). 
 Infra deduplication. Consolidated parseRetryAfterMs (3→1), waitForExit (2→1), request-auth helpers (2→1), and resolveQueue (2→1); a CREDENTIAL_KEYS loop replaces three duplicated copy blocks. 
 Worker-restart hardening via a single-spawn gate. 
 Deterministic dependency closure for the bundled plugin runtime. 
 
 Full Changelog : v13.7.0...v13.7.1