---
id: inbox_c15d578b
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t9bcsv/opus_47_truly_reminds_me_of_my_juniors_and_interns/"
author: "/u/Icemasta"
published_at: 2026-05-10T16:20:22+00:00
fetched_at: 2026-05-10T22:37:17.006356+00:00
content_hash: "9ae662a4860e9b90e396e14dfb81ed9313bf3836d99f3d1969c1fb834c04e2d8"
lang: en
caption_quality: None
raw: true
topics: []
---

# Opus 4.7 truly reminds me of my juniors and interns

I use a bunch of LLMs, I hadn't used Opus 4.7 yet, decided to try it for a project this weekend. Dear lord, it's both great and so frustrating. I am working on a discography tracking project. I have the metadata providers wired in. I made a short plan with 4.7 Opus, very straight forward: 1) When an artist is added -&gt; Call API end point for artist (contains artist info and discography) -&gt; Add to DB each album and artist info from this payload 2) A recurring process that fetches up to date information based on the album ID contained in the previous payload, to get the track list, track number, and upsert all other interesting things. It then made a good plan that followed this, I reviewed the plan with it to correct one thing.... and then it implemented it all wrong. It decided to merge 1 and 2 into one big fat stack, it would do as #1 said, but then instead of immediately writing the album info that's already received to database, it decided to pipe in #2 in it. That means album fetching was no longer a delegated async process, but literally required. This is where it reminds me of my juniors and interns the most: When I told it &quot;Hey, this drifted from the plan, please refactor into etc.....&quot; it said and I quote &quot;What was implemented is similar to what you described, what you want is a fix to ...&quot; and it's not me that put that part in bold. Never in my life have I ever wanted to punch an AI, I've had juniors do that exact same shit, you ask for something, you literally write clearly the functional requirements even down to pseudocode, they go and complete other way and then go &quot;You don't understand it's doing exactly what you asked&quot;, but not in the way I asked. inb4 skill issues, maybe it is, but I've been using a ton of models to code, both hosted locally and the big 3, and it's the first time in 5 years probably that I got genuinely pissed off at the answer. Like a model being wrong is fine. A model being wrong and then trying to gaslight you into telling you it's actually right? &#32; submitted by &#32; /u/Icemasta [link] &#32; [comments]