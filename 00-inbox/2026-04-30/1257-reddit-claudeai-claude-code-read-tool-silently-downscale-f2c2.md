---
id: inbox_2b3b37b6
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t08qow/claude_code_read_tool_silently_downscales_images/"
author: "/u/IsaacKatahdin"
published_at: 2026-04-30T20:55:01+00:00
fetched_at: 2026-05-01T12:57:19.178973+00:00
content_hash: "f2c281139be9c41389c10d20951b570fc5be883c297f09c6939fb5d2f2425c24"
lang: en
caption_quality: None
raw: true
topics: []
---

# Claude Code Read tool silently downscales images

<!-- SC_OFF --><div class="md"><p>Sent Claude Opus 4.7 a set of 10 retina screenshots (in Claude Code). Asked it to extract some text from them. Text was normal size clearly readable on my screen.</p> <p>Got back a confidence structural summary and a vague “couldn’t fully read every value” answer.</p> <p>Pushed on it. Turns out the ‘read’ tool down scales images before the model sees them. The thing I was looking at on my monitor and the thing the model was looking at were not the same image.</p> <p>No warning anywhere. The tool result is indistinguishable from reading a text file. You hand it a screenshot, get back a confident answer, and have no signal that the model is working off of degraded copy.</p> <p>So all this time whenever I gave Claude a screenshot to look at it’s been hallucinating most of the answers that I’ve been looking for?</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/IsaacKatahdin"> /u/IsaacKatahdin </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t08qow/claude_code_read_tool_silently_downscales_images/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t08qow/claude_code_read_tool_silently_downscales_images/">[comments]</a></span>