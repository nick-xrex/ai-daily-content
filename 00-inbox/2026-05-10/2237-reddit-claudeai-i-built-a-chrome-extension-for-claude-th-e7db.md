---
id: inbox_0356e0f1
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t91inn/i_built_a_chrome_extension_for_claude_that_adds/"
author: "/u/Ok_Negotiation_2587"
published_at: 2026-05-10T08:47:04+00:00
fetched_at: 2026-05-10T22:37:17.116253+00:00
content_hash: "e7db9c4c8661a5202b33c769473dcb18b63e386b8d9675c1ac3ebb9062688ebb"
lang: en
caption_quality: None
raw: true
topics: []
---

# I built a Chrome extension for Claude that adds message-level bookmarks

I'm one of the people behind Claude Toolbox, a Chrome extension specifically for claude.ai. Wanted to share it here because the bookmark feature came out of an annoyance I kept hitting myself. What it does You can bookmark any individual message inside a Claude conversation. Click to save a reply, give it a label if you want, then later click the bookmark and the page scrolls straight to that message and highlights it for a second. No more hunting through 200 messages for the code snippet Claude gave you last Tuesday. It also does full-text search across all your synced conversations and one-click export as TXT or JSON. How Claude helped me build it &quot;Used Claude Code to scaffold the IndexedDB sync layer and migration logic&quot; &quot;Claude wrote the first pass of the message-bookmark schema and the scroll-to highlight animation&quot; &quot;Debugged a race condition in the background sync with Claude by pasting the worker logs&quot; &quot;Drafted the i18n strings for all 10 locales by giving Claude the EN file and asking for one locale at a time&quot; Free to try The free tier covers full-text search and lets you bookmark messages across 2 conversations, plus background sync. That was the version I shipped first to make sure the workflow was actually useful. Paid is $5/month or $49 one-time lifetime if you want it across every conversation. Screenshot Bookmark any Claude message with one click. Works across all your conversations. Claude Toolbox bookmarks panel with saved messages and scroll-to navigation Link https://chromewebstore.google.com/detail/claude-toolbox/camddjjmcemmmlndbciaodchkodhgibh Happy to answer anything about the build or the design tradeoffs in the comments. &#32; submitted by &#32; /u/Ok_Negotiation_2587 [link] &#32; [comments]