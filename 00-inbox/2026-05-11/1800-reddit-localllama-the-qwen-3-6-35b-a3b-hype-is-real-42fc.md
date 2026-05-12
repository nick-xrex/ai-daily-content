---
id: inbox_cf1cb479
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t9whrt/the_qwen_36_35b_a3b_hype_is_real/"
author: "/u/The_Paradoxy"
published_at: 2026-05-11T07:51:34+00:00
fetched_at: 2026-05-11T18:00:38.912208+00:00
content_hash: "42fcb69098e2689b5f8355a82d6166c7e09573bdae7141fbe9cb4a0fda3b0594"
lang: en
caption_quality: None
raw: true
topics: []
---

# The Qwen 3.6 35B A3B hype is real!!!

My personal test for small local LLM intelligence is to check whether a model has any ability to understand the code that I write for my own academic research. My research is on some pretty niche topics and I doubt that anything like it is substantively present in the training sets for LLMs. A few months ago, small local models' ability to understand my code was nominal at best with Devstral Small 2 being the top performer . However, several small open weight models now have methods of accommodating fairly long contexts (gated delta net, hybrid Mamba2, sliding window attention) which makes them extremely smarter . I can now feed a model an entire academic paper along with accompanying code and ask it to use the paper to work out what the code is doing. I just spent a couple days experimenting with: Qwen 3.6 35B A3B Qwen 3.6 27B Gemma 4 26B A4B Nemotron 3 Nano All of them were able to comprehend my code significantly better than what any small local model could do a few months ago. I did try Devstral Small 2 since I recently went from a single 16GB graphics card to two; however, I simply couldn't fit the long context in 32GB of ram. I hope Mistral releases a new small model with a gated delta net, because I think it could take the throne. These are my detailed findings from asking local models to explain how my code maps to the research paper it corresponds to. TLDR: All four models listed above are incredibly capable local models, with Qwen 3.6 35B A3B standing out as the best. I'm also inclined to think that an intelligent human with any of these four models is more capable than something like Opus 4.7 on its own (see the detailed findings). Please let me know your thoughts! &#32; submitted by &#32; /u/The_Paradoxy [link] &#32; [comments]