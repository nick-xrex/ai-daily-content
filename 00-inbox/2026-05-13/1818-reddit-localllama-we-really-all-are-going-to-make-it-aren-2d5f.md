---
id: inbox_d6a75466
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tcf2dt/we_really_all_are_going_to_make_it_arent_we/"
author: "/u/RedShiftedTime"
published_at: 2026-05-13T22:25:53+00:00
fetched_at: 2026-05-14T18:18:30.402261+00:00
content_hash: "2d5f50e3129d60fe4f6e92ddb494c382eac46b11332b8cf3b2866aa1151fcd9d"
lang: en
caption_quality: None
raw: true
topics: []
---

# we really all are going to make it, aren't we? 2x3090 setup.

i'm blown away. i saw someone made a post the other day about &quot;club-3090&quot; and after having sonnet patch some fixes into it, specifically a sse-session drop bug and a bug with tool-calling, it's fair to say that even &quot;budget&quot; setups like myself will have a path forward soon for only-local-ai. reference github: https://github.com/noonghunna/club-3090 (not mine) after getting this running, i was originally using WSL2. fair to say, it was &quot;better&quot; than LM studio but not quite good. t/s was like 30 and pp was around 400....i said fuck it and installed ubuntu as dual boot on the same machien (i'm just not very linux friendly when it's headless, prefer windows RDP) and wow. i'm getting like 4000 pp/s and 113 tk/s with no nvlink. supposedly, nvlink would make it faster..... either way, i'm very excited about this new local future. qwen 3.6 27b with 262k on 48 GB VRAM feels almost-sonnet level, and it's MUCH faster than cloud. and useful! I had it make some monkey patches and they work fantastic, and well as some relatively useful code reviews. im working now on making it work to handle my ssh sessions on my linux computers now. wondering what the next upgrade path could be. i was thinking about m5 ultra 512 GB + 4x DGX Sparks (prompt processing speeeeed) but now I'm wondering if we'll reach frontier class intelligence (maybe only domain specific) in smaller models in the next 12 months? awesome! &#32; submitted by &#32; /u/RedShiftedTime [link] &#32; [comments]