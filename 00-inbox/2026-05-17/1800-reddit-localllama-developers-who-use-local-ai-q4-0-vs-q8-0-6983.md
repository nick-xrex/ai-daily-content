---
id: inbox_8a82d741
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tfqfvt/developers_who_use_local_ai_q4_0_vs_q8_0_kv_quant/"
author: "/u/Jorlen"
published_at: 2026-05-17T14:03:08+00:00
fetched_at: 2026-05-17T18:00:47.171815+00:00
content_hash: "6983018c1ded7e5ef02be6741d66750e42820a5a86c3a059ee298af4fa8afa72"
lang: en
caption_quality: None
raw: true
topics: []
---

# Developers who use local AI - Q4_0 vs Q8_0 KV quant?

I'd love to hear from developers who use big context windows if they notice a difference? Obviously I would love to cut the KV cache VRAM requirement in half, but I'm worried about quality especially when we enter into 50k+ context territory. I don't really need a full study, just wondering, anecdotally, what people have experienced. My current setup: Docker stack with Llama.cpp server at the helm (Vulkan - I pay AMD tax daily) - 32GB VRAM, using mostly Qwen 3.6 models for development. I go back and forth beetween the 27b dense and 35b MoE. WIth a dash of the lil guy (3.5 9B omnicoder variant) for smaller stuff since it's so zippy and uses a shite-ton less vram. &#32; submitted by &#32; /u/Jorlen [link] &#32; [comments]