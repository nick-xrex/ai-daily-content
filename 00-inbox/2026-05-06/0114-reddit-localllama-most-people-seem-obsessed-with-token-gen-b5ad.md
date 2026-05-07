---
id: inbox_c8970f8a
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t5o4kc/most_people_seem_obsessed_with_token_generation/"
author: "/u/wbulot"
published_at: 2026-05-06T20:02:22+00:00
fetched_at: 2026-05-07T01:14:38.461975+00:00
content_hash: "b5ad0f995f256e00485d5487aac01bf7ccf4a49c8cb941949372151c8dcd9d30"
lang: en
caption_quality: None
raw: true
topics: []
---

# Most people seem obsessed with token generation speed, but isn’t prefill the real bottleneck? Am I missing something?

<!-- SC_OFF --><div class="md"><p>I read this sub every day and I keep seeing benchmarks and discussions focused almost entirely on tokens/s generation speed. Prompt processing speed barely gets mentioned.</p> <p>From my own experience running a bunch of different models on different GPUs for all kinds of tasks, the prefill stage is usually the part that actually feels slow. Once generation starts, even “only” 15 t/s is perfectly usable for me. The wait for the model to eat the prompt is what eats most of the time.</p> <p>Seeing all the hype around MTP lately kind of reinforces that feeling. If generation speed improvements don’t really move the needle on total wall-clock time for typical use cases, why is everyone laser-focused on it?</p> <p>For example, with Qwen 27B Q6 I’m getting ~15 t/s generation with my current setup (which feels fine no matter what I’m doing) but only ~300 t/s on prefill. I spend way more time staring at the processing than I do waiting for the actual reply to finish. Even with prompt caching.</p> <p>Am I misunderstanding something about how most people use these models? Curious what others are seeing.</p> <p>Edit: I forgot to mention that I mostly do agentic work, where the model has to ingest part of the codebase before it can actually do anything useful. For normal chat this obviously isn’t an issue, context stays small and you just need enough t/s to keep up with your reading speed.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/wbulot"> /u/wbulot </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5o4kc/most_people_seem_obsessed_with_token_generation/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5o4kc/most_people_seem_obsessed_with_token_generation/">[comments]</a></span>