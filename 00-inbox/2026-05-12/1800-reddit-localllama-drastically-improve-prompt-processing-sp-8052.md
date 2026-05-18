---
id: inbox_0069283c
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tany5t/drastically_improve_prompt_processing_speed_for/"
author: "/u/coder543"
published_at: 2026-05-12T02:12:28+00:00
fetched_at: 2026-05-12T18:00:40.880689+00:00
content_hash: "8052b580833df40e04e89f2cb59112c39a94fe5dbfb6f42787d9f2dff31a7d0a"
lang: en
caption_quality: None
raw: true
topics: []
---

# Drastically improve prompt processing speed for --n-cpu-moe partially offloaded models

Bigger ubatch made gpt-oss-120b prompt processing much faster on my RTX 3090 I was tuning gpt-oss-120b-F16.gguf with llama.cpp on a 24 GB RTX 3090 and found that increasing the physical micro-batch size ( -ub ) can massively improve prompt processing throughput, as long as you also raise --n-cpu-moe enough to keep the run inside VRAM. The llama.cpp defaults are -b 2048 and -ub 512 ; I included that default run as its own point in the chart. Here are the informal llama-bench results I charted: ubatch n-cpu-moe prefill generation 256 25 240.03 tok/s 33.14 tok/s 512 (default) 26 380.27 tok/s 32.29 tok/s 2048 25 1112.54 tok/s 32.96 tok/s 4096 26 1682.47 tok/s 32.38 tok/s 8192 28 2090.68 tok/s 30.05 tok/s Compared with the llama.cpp default -ub 512 , prompt processing went from about 380 tok/s to about 2091 tok/s, roughly a 5.5x gain. Compared with the smaller -ub 256 run, it was about an 8.7x gain. Token generation dropped from about 32.3 tok/s at default settings to 30.1 tok/s at -ub 8192 , about a 7% reduction. The catch is that the larger ubatch needs more GPU compute workspace. On my machine, -ub 4096 needed --n-cpu-moe 26 , and -ub 8192 needed --n-cpu-moe 28 . So this is a throughput trade: move a few more MoE layers to CPU to make enough room for the bigger batch, and prompt-heavy workloads get dramatically faster while generation gets a little slower. https://preview.redd.it/s750judj7m0h1.png?width=2250&amp;format=png&amp;auto=webp&amp;s=c696d26db310933120b9b99c310b2662e2d4f390 Note: the first four prefill points are pp4096 ; the 8192 ubatch point is from a pp8192 run, so treat this as an informal tuning result rather than a perfectly controlled benchmark. ----- One of the reasons I bought a DGX Spark was to have better prompt processing speeds. If I had known about this trick, I might not have done that in retrospect, even though it is a very nice machine, and still gets slightly better prompt processing performance and like double the token generation speed for gpt-oss-120b. Higher ubatch drastically closes the gap. &#32; submitted by &#32; /u/coder543 [link] &#32; [comments]