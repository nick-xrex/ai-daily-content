---
id: inbox_5441eb85
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t7mdrl/mtp_is_all_about_acceptance_rate/"
author: "/u/Hydroskeletal"
published_at: 2026-05-08T22:11:38+00:00
fetched_at: 2026-05-09T01:51:59.659640+00:00
content_hash: "14e467cefc052dbb8a756a24d1092a2078f3aab49f3a1ce3a4449431f076757d"
lang: en
caption_quality: None
raw: true
topics: []
---

# MTP is all about acceptance rate

So I was very excited about the MTP stuff especially since Gemma4 has become my &quot;daily driver&quot; for some stuff. I grabbed the latest mlx-vlm and did some tests and found it disappointing. Workload MTP off MTP on Result Draft accept rate Code generation 75 tok/s 114.8 tok/s 1.53× faster 66% of slots Long-form prose 75 tok/s 71.1 tok/s 0.95× (wash) 31% of slots JSON output 51.3 tok/s 25.6 tok/s 0.50× slower 8% of slots Code generation was the typical &quot;Write some python functions to do X&quot; Long form prose was &quot;Write an 800 word essay on paper money in the Tang Dynasty&quot; JSON output was my core use case where I'm handing the LLM a list of items, asking it to group them by similarity according to some rules and then get them back in a structured output*. So if you want to use it for local coding, MTP is great. If you're not, maybe not so hot. My regression testing seems to indicate that once token acceptance dips below 50% the overhead kills the benefit. All this on an M4 Max Studio w/Gemma4-26b-a4b *Bonus for you hackers: Gemma's JSON structure instruction following is pretty good and I find using structured output to be about a 20% hit to token generation. It is faster to just accept a little bit of sloppy JSON and massage it at runtime; so all this is with json_schema off which mlx-vlm doesn't support for spec-decode anyway &#32; submitted by &#32; /u/Hydroskeletal [link] &#32; [comments]