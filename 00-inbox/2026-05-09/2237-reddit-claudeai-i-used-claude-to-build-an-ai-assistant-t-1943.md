---
id: inbox_c3603b4c
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t8pwjw/i_used_claude_to_build_an_ai_assistant_that_helps/"
author: "/u/Independent-Soft2330"
published_at: 2026-05-09T23:03:47+00:00
fetched_at: 2026-05-10T22:37:17.116793+00:00
content_hash: "194386bf3a1d9f0a71dd7cb8ffc832633a96af33ed370ac864ed849cea468397"
lang: en
caption_quality: None
raw: true
topics: []
---

# I used Claude to build an AI assistant that helps run live TTRPG sessions and am looking for a few playtest GMs

Hey everyone, I’m Ted. I’ve been building a project called Throughline with my friend Drew: an AI assistant for live tabletop RPG sessions. Notes on how i built it at the bottom. How it works: while the GM runs the table, talks to players, makes taste judgments, improvises, Throughline sits behind the screen. It listens to the session, tracks what is happening, and quietly generates useful GM-facing material while the game is running: possible next scene beats, NPC/faction continuity, unresolved threads, diagrams, and storyboards for where the session might go next. I use Deepseek V4 pro for the session runner, soniox for the transcription, and GPT Image 2 on the lowest quality and pixel count (this is a hack— images cost $0.006 each and can handle way more instruction than 3.1 flash image at $0.045/image) The goal is to make a tool that helps with the planning and narrative continuity challenge of DMing. I’ve run several playtests so far, and it works well. It is especially good for social/improv-heavy sessions where the story can branch in several directions and the GM needs help keeping the world coherent. I’m looking for a few playtesters who are comfortable with AI tools and would be interested in trying it for a one-shot or short session. I’m not charging for these playtests. I mainly want honest feedback from people who actually run games. The ideal tester is probably someone who: - GMs D&amp;D or another TTRPG - likes improvisational / narrative play - has felt “too many open threads in my story right now” - is open-minded about AI as a tool, but not looking to replace the human GM The site is here: https://throughline.gg There’s more detail there about how it works. If this sounds interesting, comment or DM me, or sign up on the website. I’d love to get a few real tables using it and learn where it helps, where it gets in the way, and what it would need to become something GMs would actually want in their regular toolkit. Notes on how I built it: my day job is the CTO at a startup where i use claude code all day every day. A lot of the work in this project was in the design— for 4.7 opus, its not that complex code-wise, but its VERY out of distribution. There was a lot of work making sure my instructions for how the system should function actually made it into the repo, rather than claude compressing it. &#32; submitted by &#32; /u/Independent-Soft2330 [link] &#32; [comments]