---
id: inbox_8f330dc8
source: superpowers-releases
source_type: rss
url: "https://github.com/obra/superpowers/releases/tag/v6.1.1"
author: "obra"
published_at: 2026-07-02T21:58:30+00:00
fetched_at: 2026-07-02T22:00:24.611014+00:00
content_hash: "7186cca110b40f7deb43709b97f8f43466b07669495a9426639a7c29e66b8290"
lang: en
caption_quality: None
raw: true
topics: []
---

# v6.1.1

v6.1.1 (2026-07-02) 
 Codex 
 
 Codex no longer re-registers the Claude SessionStart hook. v6.1.0 removed the Codex hook config and its manifest hooks pointer, meaning to stop Codex from installing a SessionStart hook — but with no hooks field, Codex fell back to auto-discovering hooks/hooks.json , the Claude Code SessionStart hook that the marketplace ships from the repo root, and re-registered it along with its install-time trust prompt. The Codex manifest now declares an explicit empty hooks object ( hooks: {} ), which Codex reads as "no hooks" instead of reaching the auto-discovery fallback. An absent field, [] , and an empty inline list all collapse back to the fallback, so the value has to be exactly {} . 
 Removed orphaned Codex session-start dead code. hooks/session-start-codex had no caller once the Codex hook config was deleted, so it and its redundant test cases are gone. The worked shell-hook example in docs/porting-to-a-new-harness.md moves from Codex — now native skill discovery with no session-start hook — to Cursor, a live shell-hook harness, and the stale hooks-codex.json pointer in docs/windows/polyglot-hooks.md is corrected. The Codex plugin category is also fixed to "Developer Tools". 
 
 Packaging 
 
 New package-codex-plugin.sh for building the Codex portal package. A maintainer script produces a deterministic Codex "portal" archive — .zip by default, tar.gz on request — that normalizes entry timestamps, preserves executable modes, verifies every packaged skill ships its OpenAI metadata, includes the app and composer icons, and refuses to run against a dirty worktree. The packaged manifest keeps the source hooks: {} object so a portal-installed plugin avoids the same SessionStart auto-discovery, and the script can rebuild a byte-identical archive from a saved metadata source. Covered by a new test suite.