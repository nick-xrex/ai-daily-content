---
id: inbox_3ddd6446
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t9e2xw/built_html_drive_google_drive_for_claude/"
author: "/u/invocation02"
published_at: 2026-05-10T18:02:28+00:00
fetched_at: 2026-05-10T22:37:17.115749+00:00
content_hash: "c058deb951d0b1a1b925a45abd0b1a08bba1d9db03ad5252f4a931dc3691940f"
lang: en
caption_quality: None
raw: true
topics: []
---

# Built HTML Drive - Google Drive for Claude generated HTML files

I built HTML Drive this weekend: a personal Drive Claude can save to. Sign in with Google, then ask Claude to make HTML and it lands in your account, versioned, shareable, and with its own URL. The reason I built it is Thariq Shihipar's (Anthropic engineer) argument that markdown is restricting. Anyone who's watched Claude produce a 500-line markdown plan knows nobody actually reads it. HTML is what Claude does its best work in — colors, layout, interactivity, illustrations — but HTML files don't have a default home the way markdown does. They are somewhere in your filesys, or you upload them to S3 and lose track, or you screenshot the rendered version and lose all the interactivity. I wanted somewhere I could just point Claude at and say &quot;save it there.&quot; Connecting your agent is dead simple. You click &quot;Connect agent&quot; in the toolbar and get a single URL. You paste that URL into Claude Code. That's the entire setup. Behind the scenes the URL points to instructions the server generates on the fly with your credentials baked in, so the agent fetches it once and immediately knows how to save HTML to your account. No environment variables, no separate config files, no two-step paste. Just one URL. Every save is versioned automatically, so older versions stay reachable while the latest is what loads when someone visits the share link. Sharing works like Google Docs: private by default, invite specific people by email, or flip the whole thing public. There are folders for organizing, and the file browser has both an icon view (with little live previews of each file) and a list view. For demos, I had Claude render Thariq's essay as the kind of HTML it argues for: a living document with interactive figures sprinkled through, instead of a flat markdown blob. I also asked Claude to write a devlog while it was building the Drive, and we saved it into the Drive it was building. Both are public on the homepage. Try it: https://html.app.teenyapp.com &#32; submitted by &#32; /u/invocation02 [link] &#32; [comments]