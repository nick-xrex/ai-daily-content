---
id: inbox_6cc7055b
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.13.3"
author: "ruvnet"
published_at: 2026-06-22T18:01:13+00:00
fetched_at: 2026-06-22T22:03:43.571344+00:00
content_hash: "a463d21550b64469f00fbfe086b0f32dbf0797009dba8f70fc6cd5c74d7c94c0"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.13.3 — #2448 stale npx @latest statusLine/hooks migration (kernel-panic class)

🔧 Critical fix — #2448 
 Affected user reported load average 49 / jetsam / kernel watchdog panic on macOS. Pre- #2337 init wrote `npx @claude-flow/cli@latest hooks ` into the statusLine + per-action hooks. Each invocation cold-spawns ~130 MB Node + npm registry round-trip; statusLine refires every few hundred ms. 
 The current init source already emits the local-helper form — but `executor.ts:362` preserved the user's existing command on re-init, so anyone who installed pre- #2337 and upgraded never received the fix. 
 Two changes 
 
 init migration: detect the broken `npx @latest hooks ` pattern in `existing.statusLine.command` AND every `hooks.[].hooks[].command`. Regenerate to local-helper form. Idempotent on already-correct settings. Captures the subcommand from the broken string so intent is preserved. 
 doctor check: new `checkStaleSettingsNpx` reports `fail` if the broken pattern is detected anywhere in project-local or `$HOME/.claude/settings.json`. Run `ruflo doctor --component stale-settings` to check directly. 
 
 How to recover if you're affected 
 ```bash 
 Detect (no changes) 
 npx ruflo@latest doctor --component stale-settings 
 Migrate (re-runs init merge logic, regenerates the broken commands) 
 npx ruflo@latest init 
 Verify 
 npx ruflo@latest doctor --component stale-settings # should now ✓ 
``` 
 Distribution 
 
 
 
 Package 
 latest 
 alpha 
 v3alpha 
 
 
 
 
 `@claude-flow/cli` 
 3.13.3 
 3.13.3 
 3.13.3 
 
 
 `claude-flow` 
 3.13.3 
 3.13.3 
 3.13.3 
 
 
 `ruflo` 
 3.13.3 
 3.13.3 
 3.13.3 
 
 
 
 Cross-references 
 
 🔗 Issue: #2448 (CRITICAL, closed) 
 🔗 Prior partial fix: #2337 (statusline storm) — fixed the generator but not the upgrade path 
 🔗 Companion: #2443 (doctor MetaHarness locator), #2444 (sql.js MEMFS leak) 
 
 
 🤖 Generated with RuFlo