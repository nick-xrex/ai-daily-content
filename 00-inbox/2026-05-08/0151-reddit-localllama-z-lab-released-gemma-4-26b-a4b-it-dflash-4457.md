---
id: inbox_973738bf
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t79ayh/zlab_released_gemma426ba4bitdflash_anybody_tried/"
author: "/u/PaceZealousideal6091"
published_at: 2026-05-08T14:18:09+00:00
fetched_at: 2026-05-09T01:51:59.613562+00:00
content_hash: "4457220dc8b251c6b5d6f54c94b9b5440d93d99ce857e2cc35568cde47ad6013"
lang: en
caption_quality: None
raw: true
topics: []
---

# z-lab released gemma-4-26B-A4B-it-DFlash. Anybody tried it yet?

Past few days, its all been about MTPs. Somehow people missed out the fact that Z lab released the Dflash for Gemma4 26B a couple of days ago. As far as my understanding goes, Dflash should be a better alternative than MTP because of faster parallel block diffusion drafting and the fact that it is stateful (it can have a persistent state across iterations for context buffers, KV cache positions, and RoPE offsets). This basically should mean that dflash should be drastically better as the session extends and context grows. MTP should technically degrade faster because the kv cache will start balooning faster. I am very curious though how much of a speed difference does dflash bring to sparse models like Gemma 4 26B and Qwen 3.6 35B. Unfortunately, I can't test it since it's vllm only . Anybody tried using this? Any significant gains in speed? And what's the state of dflash support over lcpp? Are we any close? &#32; submitted by &#32; /u/PaceZealousideal6091 [link] &#32; [comments]