---
id: inbox_a59f8784
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.11"
author: "ruvnet"
published_at: 2026-07-26T22:49:38+00:00
fetched_at: 2026-07-27T01:23:04.179998+00:00
content_hash: "613dc4a1d78ecd1b6004edd31b035f9ac21be6de0df09e89d469b730711c9f83"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.11 — bridgeRecordFeedback wired to real intelligence pipeline (#2786 fix-3)

Follow-up patch closing the last remaining item flagged by the 2026-07-26 tracker-sweep agent — the sweep tagged it "architectural" but investigation showed a much smaller surgical fix was available. 
 Fixed 
 
 #2786 fix-3 — bridgeRecordFeedback no longer silently swallows every call. The prior code called learningSystem.recordFeedback / .record and reasoningBank.recordOutcome / .record , but the registry actually wires the LOCAL intelligence classes ( LocalSonaCoordinator / LocalReasoningBank ) via initializeIntelligence() in memory/intelligence.ts — those classes never had those methods, and two catch { /* API mismatch — skip */ } blocks made the failure invisible. Fix: call the real public API intelligence.recordTrajectory(steps, verdict) — same call hooks_post-command already uses. Pattern-store branch also fixed to call LocalReasoningBank.store(pattern) (the one method that actually exists). No mocks, no silent catches on the happy path. 
 
 E2E verification (no mocks) 
 Fresh scratch cwd, memory init + 3× hooks post-task --task ... --store-results true : 
 
 Before: hooks intelligence stats → 0 trajectories 
 After: 6 trajectories on disk + 3 pattern entries ( ~/.claude-flow/neural/stats.json ) 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.11 
 Closes: #2786 (the last remaining fix from the 2026-07-26 sweep).