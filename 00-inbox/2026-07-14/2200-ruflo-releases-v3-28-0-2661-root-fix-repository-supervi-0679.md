---
id: inbox_182e123b
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.28.0"
author: "ruvnet"
published_at: 2026-07-14T05:36:54+00:00
fetched_at: 2026-07-14T22:00:25.104191+00:00
content_hash: "067909dc63619deab0b68f73dfa2385b32e0c38e0330913814b03416b9630592"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.28.0 — #2661 root-fix: repository supervisor, telemetry, budget CLI, migration warning

Highlights 
 Closes the four remaining root-fix gaps from #2661 (PR #2663 ): 
 
 Repository-level supervisor + worktree leases ( workspace-lease.ts , repo-supervisor.ts ) — exactly one daemon per repository is elected supervisor and owns the recurring AI-worker schedule; every other worktree stays a lease-only participant (15-min TTL heartbeat) running cheap local-only workers. An explicit daemon trigger --headless still bypasses the gate (one-off user action, still budget/dedup-governed). 
 Structured per-launch token telemetry — claude --print --output-format json , parsed leniently via parseClaudePrintJsonEnvelope() , receipted through GlobalAiBudget.recordUsage() . Any schema mismatch degrades to "no usage captured," never breaks existing analysis-output parsing. 
 ruflo daemon budget show|pause|resume — independently scriptable budget control surface. 
 One-time upgrade migration warning — a pre-existing multi-daemon fleet with AI workers already enabled warns exactly once ever. 
 
 daemon status --all gains a "Repository Supervisors" panel. 
 Also fixes a real transitive-dependency fragility: statusline-generator.ts no longer pulls in the semver package just to resolve the CLI's own version — inlined a minimal, dependency-free version resolver instead. 
 Test plan 
 
 54 new tests across workspace-lease , repo-supervisor , claude-print-envelope , global-ai-budget , daemon-migration-warning-2661 
 636 relevant tests passing locally (services + daemon + commands-deep) 
 Full CI green on PR #2663 (one flaky, unrelated timing test in @claude-flow/hooks 's trajectory-graph smoke passed on rerun) 
 
 Packages 
 
 
 
 Package 
 Version 
 
 
 
 
 @claude-flow/cli 
 3.28.0 
 
 
 claude-flow 
 3.28.0 
 
 
 ruflo 
 3.28.0