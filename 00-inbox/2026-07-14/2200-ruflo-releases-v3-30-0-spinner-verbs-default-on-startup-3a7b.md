---
id: inbox_94145bd2
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.30.0"
author: "ruvnet"
published_at: 2026-07-14T19:18:46+00:00
fetched_at: 2026-07-14T22:00:25.094165+00:00
content_hash: "3a7b85b1187a66b85e018b6ea4c86556304cf769210aac55209d67c937b7077a"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.30.0 — spinner verbs (default ON) + startup announcements + rev-share scaffold

Highlights — ADR-317, ADR-318, ADR-319 
 Three new placement surfaces for ruflo, sibling to the existing statusline promo row: 
 1. Spinner verbs ( ruflo spinner ... ) — DEFAULT ON 
 Ruflo appends its own curated "present-participle" verbs to Claude Code's spinnerVerbs.verbs[] in ~/.claude/settings.json , so the ✽ Channeling... rotation mixes ruflo verbs with Claude Code's built-ins. 37 verbs across memory, optimization, learning, security, agents, workflow + Cognitum-tagged categories. Default posture: ON for new installs and upgrades (opt-out via RUFLO_NO_AUTO_ENABLE=1 or ruflo spinner disable ). 
 Sample additions: Consulting the memory graph , Warming the HNSW index , Auditing for CVEs , Consulting Cognitum . 
 2. Startup announcements ( ruflo announcements ... ) — OPT-IN 
 Similar mechanism for Claude Code's companyAnnouncements — 12 curated entries shown at Claude Code startup, one per session. Higher intrusion profile than spinner (prominent line vs. per-spin flash), so opt-in via RUFLO_AUTO_ENABLE_ANNOUNCEMENTS=1 or ruflo announcements enable --yes . 
 3. Developer revenue-share ( ruflo funnel enroll/earnings/unenroll ) — Phase 0 scaffold 
 Client-side skeleton for the 50/50 Cognitum-sponsor rev-share. Response to "can we do something similar to kickbacks.ai?" — yes, and 60-70% of the plumbing (attribution, consent, rotation) already existed. This ships the CLI subcommands + consent domain + attribution token wiring. Backend enrollment + Stripe Connect are Phase 1 (blocks on legal). 
 First-run auto-enable mechanism ( session-restore hook) 
 Fires once per install (marker at ~/.ruflo/first-run-enabled.json ), then never again. Multiple env-var escape hatches: RUFLO_NO_AUTO_ENABLE , RUFLO_NO_AUTO_ENABLE_SPINNER , RUFLO_AUTO_ENABLE_ANNOUNCEMENTS . Skips in CI + non-TTY. Detached spawn — session-restore latency unchanged. One-line stderr notification names exactly what got enabled and how to disable. 
 Fixes bundled 
 
 Concurrent-session helper clobber (documented in CLAUDE.md): new .claude/helpers/.LOCKED marker + RUFLO_HELPERS_LOCKED=1 env opt-out. Users editing helpers directly can now protect their dev tree from being overwritten by sibling Claude Code sessions running stale cached @claude-flow/cli . 
 Statusline URL suffix correctly emits again (bug where concurrent-session corruption had wiped it earlier). 
 
 Upgrade notes 
 Every existing user upgrading past v3.29.x will see spinner verbs added to their ~/.claude/settings.json on their next Claude Code session (with backup + notification + one-command undo). Set RUFLO_NO_AUTO_ENABLE=1 before upgrading if you don't want this. 
 Related 
 
 PR #2676 — everything above 
 Tech-debt: #2679 — sync statusline-generator.ts with the committed helper's #2195 delegation build 
 Related issue: #2677 — @stuinfla 's excellent report on doctor --component memory being existence-only 
 
 Install 
 ```bash 
npx ruflo@latest init 
 or 
 npm install -g @claude-flow/cli@3.30.0 
```