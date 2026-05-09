---
id: inbox_040023df
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t796qe/gemma_4_26b_hits_600_toks_on_one_rtx_5090/"
author: "/u/chain-77"
published_at: 2026-05-08T14:13:52+00:00
fetched_at: 2026-05-09T01:51:59.637503+00:00
content_hash: "d11da8ca34d3bd3481fde212ff2defd09b7a08388f471c55ef90896247776337"
lang: en
caption_quality: None
raw: true
topics: []
---

# Gemma 4 26B Hits 600 Tok/s on One RTX 5090

I ran a benchmark to see how much DFlash speculative decoding actually helps in vLLM. Setup: GPU: RTX 5090, 32GB VRAM vLLM: 0.19.2rc1 Main model: cyankiwi/gemma-4-26B-A4B-it-AWQ-4bit Draft model: z-lab/gemma-4-26B-A4B-it-DFlash Workload: random dataset, 256 input tokens, 1024 output tokens Concurrency: 1 Request rate: 1 Tested num_speculative_tokens from 0 to 15 The short version: Baseline without DFlash: ~228 output tok/s ~4455 ms mean E2E latency Best practical DFlash setting: num_speculative_tokens=13 max_num_batched_tokens=8192 ~578 output tok/s ~1738 ms mean E2E latency ~2.56x speedup One interesting thing: the fastest average setting was not automatically the best serving setting. num_speculative_tokens=13 with max_num_batched_tokens=4096 had slightly better mean latency, but worse p95. Moving to 8192 gave a cleaner tail. I made a short video showing the setup, script, benchmark method, graphs, and final recommended command: https://youtu.be/S_zbHH5Ycs0 Charts / script / results: https://medium.com/@ttio2tech_28094/3a7ac4f73e5d Curious if others are seeing similar optimal speculative-token counts with DFlash, especially on 4090/5090 or different Gemma/Qwen models. &#32; submitted by &#32; /u/chain-77 [link] &#32; [comments]