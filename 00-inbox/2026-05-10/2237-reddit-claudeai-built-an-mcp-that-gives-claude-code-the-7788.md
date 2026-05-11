---
id: inbox_b13e919b
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t9frna/built_an_mcp_that_gives_claude_code_the_ability/"
author: "/u/ashadis"
published_at: 2026-05-10T19:04:30+00:00
fetched_at: 2026-05-10T22:37:17.077313+00:00
content_hash: "7788c192c50829d56d8f01539ba1f43b1d1c1887d45c5021dcd4dc6f9c1e16e7"
lang: en
caption_quality: None
raw: true
topics: []
---

# Built an MCP that gives Claude Code the ability to watch screen recordings of UI bugs

One thing Claude Code can't do natively is watch a video. For most bugs that's fine, but for anything visual, hover states, animations, scroll behavior, you end up spending more time describing the bug than actually fixing it. I built motif to handle this. You record the bug, point motif at the file, and it returns what's visually happening, the root cause, and a diff. It uses Gemini 2.5 Flash as it processes video as a frame sequence rather than a single screenshot. That distinction matters when the bug is a 200ms overshoot or a hover state that resets at the wrong time. Setup is a Gemini API key and two lines in your mcp.json. After that you just tell Claude Code to watch the recording.That's the whole interface. npx motif-mcp to try it. Repo: https://github.com/Ashad001/motif , still early so feedback is welcome. https://reddit.com/link/1t9frna/video/xd83w09fyc0h1/player &#32; submitted by &#32; /u/ashadis [link] &#32; [comments]