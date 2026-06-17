---
id: inbox_c7e84ab9
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.179"
author: "ashwin-ant"
published_at: 2026-06-16T20:22:14+00:00
fetched_at: 2026-06-16T22:00:14.094068+00:00
content_hash: "94f5983b0432fe68ec49bde5715aa0039dc4a0fb13e15dab14a4809bb92ad90b"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.179

What's changed 
 
 Fixed mid-stream connection drops: partial responses are now preserved instead of showing a raw error, and the spinner no longer gets stuck at "running tool" 
 Fixed mouse-wheel scrolling in WSL2 under Windows Terminal and VS Code (regression in 2.1.172) 
 Fixed a sandbox denyRead / allowRead glob over a large directory tree making the Bash tool description enormous and the session unusable on Linux 
 Fixed the feedback survey capturing a single-digit reply as a session rating immediately after a turn completes 
 Fixed the welcome screen stacking multiple promotional banners — at most one promo now shows per session 
 Fixed Ctrl+O not showing the subagent's transcript when viewing a subagent 
 Fixed clicking the prompt input not returning focus from the subagent/footer panel 
 Fixed remote session background tasks appearing stuck as "still running" between turns 
 Improved plugin loading performance in remote sessions