---
id: inbox_cc7bef6a
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.26.1"
author: "ruvnet"
published_at: 2026-07-13T17:22:41+00:00
fetched_at: 2026-07-13T22:31:53.151960+00:00
content_hash: "9b3dec18469926423ad5469df5855a247a1fbc73a8c15dbc03ed8a5aaa78ab8d"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.26.1 — Windows statusline hotfix

Fix 
 Fixes a real bug reported by a Windows user: the statusline was only showing 2 lines (missing the 
promo/insight row) with the intelligence percentage stuck at 0%. 
 Root cause: the statusline's CLI delegation command appended 2&gt;/dev/null to every candidate 
command. Node's execSync already captures/discards stderr via stdio: ['pipe','pipe','pipe'] 
regardless of shell, so the redirect was redundant on POSIX — and actively broken on Windows, where 
 cmd.exe (execSync's default shell) doesn't understand /dev/null . Every delegation attempt failed 
silently, so every render fell back to a hardcoded 0% intelligence value, and since the promo memo 
cache is only ever seeded by a successful delegation, the promo row could never populate either. 
 Pre-existing since the #2337 delegation-caching fix (2026-06-10) — not introduced in 3.26.0, just 
surfaced by a real user on that release. Fixed by removing the redundant redirect; added a regression 
test pinning it can't come back. 
 Known follow-up (not fixed here): getGitInfo() still uses a POSIX-only sh -c script to read 
the git username/branch shown in the header — will show generic "user" with no branch on native 
Windows. Separate, smaller-impact issue, left out of this hotfix to keep it minimal and reviewable. 
 Packages published 
 @claude-flow/cli@3.26.1 , claude-flow@3.26.1 , ruflo@3.26.1 — latest / alpha / v3alpha dist-tags 
all aligned.