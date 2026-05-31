---
id: inbox_1413a8e5
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.31"
author: "ruvnet"
published_at: 2026-05-31T14:49:49+00:00
fetched_at: 2026-05-31T18:01:16.403972+00:00
content_hash: "2cdf3f2ac43b59d1df14526c3e9af3c529843900552655298e02cdfe9941118f"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.31 — model router + daemon trigger bug-fix patch (#2250, #2251)

Bug fixes 
 #2250 — model router escalation overrode Thompson bandit 
 Trained opus-suppressed priors were discarded by an "escalate one tier up" step that fired on ~every trivial route (the uncertainty formula was structurally &gt;0.6, gate at 0.15). Reporter ( @grym3s ) measured opus selected ~40% on trivial tasks, haiku never selected. 
 Fix in v3/@claude-flow/cli/src/ruvector/model-router.ts : 
 
 Escalation now skips when (a) target mean is meaningfully worse than selected ( &lt; selected_mean − 0.10 ), OR (b) selected has confident+decent posterior ( α+β ≥ 5 AND mean ≥ 0.45 ) 
 Cold-start Beta(1,1) priors fail both checks → unlearned routers preserve original conservative behavior 
 New env override: CLAUDE_FLOW_MAX_UNCERTAINTY=0.0..1.0 
 
 #2251 — daemon trigger -w &lt;worker&gt; raced headless init 
 Constructor kicked off initHeadlessExecutor() fire-and-forget. On-demand daemon trigger called triggerWorker() immediately after construction, raced the init, and fell through to the local stub in ~2ms. Scheduled fires were unaffected (long-running daemon never raced). Reporter ( @shaharKeisarApps ). 
 Fix in v3/@claude-flow/cli/src/services/worker-daemon.ts : 
 
 New headlessInitPromise field capturing the constructor's init promise 
 triggerWorker() awaits it before checking headlessAvailable 
 
 Regression guard 
 v3/@claude-flow/cli/__tests__/issue-2250-2251-regression.test.ts — 4 new tests: 
 
 Loads reporter's exact suppressed-opus prior, asserts opus rate &lt;20% AND haiku selected ≥1 time over 50 trivial routes 
 Cold-start preservation 
 Env override 
 Deferred-promise harness proves executeWorker() cannot fire until headlessInitPromise resolves 
 
 All 12 router + daemon tests pass. TypeScript clean. 
 Install 
 npx ruflo@latest # or @alpha / @v3alpha 
npx @claude-flow/cli@latest
npx claude-flow@latest 
 All three packages published to npm, all three dist-tags ( latest , alpha , v3alpha ) pointing at 3.10.31. 
 What's NOT in this release 
 5-dataset BEIR benchmark work (TREC-COVID ingest still in flight) → ships as 3.10.32.