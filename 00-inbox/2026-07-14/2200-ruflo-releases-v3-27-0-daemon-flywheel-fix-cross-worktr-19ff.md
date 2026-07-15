---
id: inbox_bc4298c6
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.27.0"
author: "ruvnet"
published_at: 2026-07-14T04:47:07+00:00
fetched_at: 2026-07-14T22:00:25.111508+00:00
content_hash: "19ff03f471c3506f14cbf71808fd51648e9b360f74b2cdd0ffb8921134a5ddf2"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.27.0 — daemon flywheel fix (cross-worktree dedup + global launch budget)

Highlights 
 Daemon flywheel fix ( #2661 ) — opt-in AI workers, a global cross-daemon launch budget, cross-worktree job dedup, and daemon stop --all . Fixes the cardinality bug where N git worktrees of one repository scheduled N independent, uncapped AI worker launches. 
 
 git-workspace-identity.ts — resolves a stable repositoryId shared across all worktrees of one repo (via git rev-parse --git-common-dir ), separate from the per-worktree path. 
 ai-job-dedup.ts — cross-worktree job dedup keyed on sha256(repositoryId, head, workerType, configHash) , backed by a shared registry at ~/.claude-flow/ai-jobs.json . 
 global-ai-budget.ts — a global launch budget (max concurrent + hourly cap) shared by every daemon on the machine, so the dedup optimization has a hard backstop even when two daemons race the same key. 
 AI workers are now opt-in rather than auto-launching. 
 daemon stop --all stops every daemon instance, not just the one bound to the current cwd. 
 
 Hook-handler fallback fix — the inline hook-handler.cjs fallback template (used when copying the real package helper fails) now spawns the funnel-refresh helper from session-restore , matching the fix already shipped in the hand-maintained helper. 
 Verified after publish 
 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) live at 3.27.0 on latest / alpha / v3alpha . 
 Confirmed the macOS jetsam-kill/kernel-panic statusline fix ( #2448 ) is intact: a real npx @claude-flow/cli@3.27.0 init produces a settings.json with zero npx @claude-flow/cli@latest invocations in any hook or the statusline — everything resolves a local binary directly via node . 
 
 Packages 
 
 
 
 Package 
 Version 
 
 
 
 
 @claude-flow/cli 
 3.27.0 
 
 
 claude-flow 
 3.27.0 
 
 
 ruflo 
 3.27.0 
 
 
 
 Follow-up 
 
 Full technical writeup of the daemon flywheel bug + fix: https://gist.github.com/ruvnet/f4cda824aaf58e1f2dae72368e692220 
 Issue thread + implementation-vs-spec gap notes: #2661 
 Follow-up fixes landed in v3.27.1–v3.27.4: marketplace-checkout install validation ( dist/src/index.js check + npx fallback for the funnel/advisor refresh), version-display max-candidate selection, baked-in version fallback for pure-npx renders, and persistent AgentDB memory on by default at init time.