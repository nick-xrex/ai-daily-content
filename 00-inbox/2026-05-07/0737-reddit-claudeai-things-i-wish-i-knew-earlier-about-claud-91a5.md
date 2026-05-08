---
id: inbox_c63a4866
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t6asgc/things_i_wish_i_knew_earlier_about_claude_token/"
author: "/u/Marmelab"
published_at: 2026-05-07T13:36:35+00:00
fetched_at: 2026-05-08T07:37:42.316042+00:00
content_hash: "91a551a19319e8b5842e6bcaf080348af9b88a2f3915a156ab90df1c891f70d1"
lang: en
caption_quality: None
raw: true
topics: []
---

# Things I wish I knew earlier about Claude token usage

A few weeks ago, I shared some tips on my Claude Code workflow. In the comments, quite a few people mentioned that they were burning through their tokens super fast and tbh I could totally relate. This is something I particularly struggled with at the beginning, which pushed me to take a closer look at it. Turns out most of my token usage wasn't coming from Claude's answers, but from the setup. Things I actually use: Start a new chat for unrelated tasks. Every message in a long conversation resends the full history. That's not obvious until I realize a 40-message thread is burning tokens on context I stopped caring about 20 messages ago. Group your small questions into one message. Sending three quick follow-ups instead of one combined message means three full context loads. I group them now and it adds up fast. Keep your CLAUDE.md short and use it as an index. I used to dump everything in there. The problem is Claude rereads it every single turn. Now it points to separate files and only loads what's relevant to the task. Things I try to implement as much as possible: Be precise with file references. I used to say &quot;here's the whole codebase, figure it out.&quot; Claude would spend 30-50k tokens just exploring before doing anything useful. Now I point it at the one function or module that actually matters. Summarize and restart after 15-20 messages. I ask Claude for a quick summary of where things stand, paste it into a fresh thread. I lose nothing and stop dragging dead context around. Use lighter models for lighter work. Not everything needs the heaviest model. Drafting, reformatting, explaining. I route those elsewhere and save the big model for the reasoning-heavy stuff. What are your go-to tricks for keeping usage under control? &#32; submitted by &#32; /u/Marmelab [link] &#32; [comments]