---
id: inbox_b68b18a9
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.2.0"
author: "thedotmack"
published_at: 2026-05-12T01:44:07+00:00
fetched_at: 2026-05-26T00:14:50.180874+00:00
content_hash: "4a922791deb986320b75a7757beae717f6783b9e922621cc2425b7e6bb001b53"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.2.0

What's new 
 wowerpoint skill — kawaii NotebookLM slide-deck generator 
 Turn one source document into a kawaii NotebookLM slide-deck PDF. Wraps the notebooklm CLI with the kawaii-prompt + --format detailed defaults and a spawn-subagent pattern so generation (~10 min) never blocks the main conversation. 
 
 Single-source-per-deck is enforced by the workflow shape: confirm or write the source doc before adding it to NotebookLM. Don't paper over a weak source by stacking more sources — write a comprehensive doc first. 
 Slide-deck only. Videos and podcasts from the same engine are noticeably worse and out of scope; the skill refers users to the notebooklm CLI directly for those formats. 
 Default prompt template: Use kawaii characters to tell the story of &lt;subject&gt;. Keep it warm and clear. Pass any user-supplied prompt through verbatim. 
 Setup requires notebooklm-py (via uv tool install --with playwright ), playwright install chromium , and jq . 
 Spawn-and-end-turn pattern: the subagent's completion notification fires when the PDF is on disk; the main conversation never blocks on the ~10 min render. 
 
 See PR #2430 for the full design notes and review history. 
 Skills inventory 
 This release brings the plugin to 12 skills : babysit, do, how-it-works, knowledge-agent, learn-codebase, make-plan, mem-search, pathfinder, smart-explore, timeline-report, version-bump, wowerpoint.