---
id: inbox_de4eb117
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1ta7p6e/anyone_with_4x_5060ti_based_setups/"
author: "/u/ziphnor"
published_at: 2026-05-11T16:04:00+00:00
fetched_at: 2026-05-11T18:00:38.981647+00:00
content_hash: "1819fef8504e0f0b566659fa7a7174fe0cb4ddf14a174e760d531a7db38d3199"
lang: en
caption_quality: None
raw: true
topics: []
---

# Anyone with 4x 5060ti based setups?

I am currently running 2x RTX 5060 ti and happened across some good sales for additional ones coinciding with a really good sale of a highend Z890 motherboard (replacing my B860 board) that could support quad GPUs (with 2 M.2 adapters, ending with running 1 GPU at 5.0 x8 and the rest at 5.0 x4, all via CPU lanes). 2x 5060 ti 16gb discounted is about the same price (~960€) as 1 used 3090 (most i can find are actuall ~1000€). I am wondering how such a quad 5060 setup compares to dual RTX 3090 in prefill and generation speed (on higher quality quants of Qwen 3.6 27B for example, like int8 / fp8)? RTX 5060 ti can easily OC memory (+3000Mhz), providing close to 500gb/s bandwidth, so looking at bandwidth per GB, its pretty close overall, and looking at FP8 TFLOPs the 5060 also comes out ahead. However, tensor parallelism is not exactly perfect scaling so I am curious where it ends up. &#32; submitted by &#32; /u/ziphnor [link] &#32; [comments]