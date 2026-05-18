---
id: inbox_f83755ce
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1td9stc/llamacpp_constantly_reprocessing_huge_prompts/"
author: "/u/No_Algae1753"
published_at: 2026-05-14T20:11:39+00:00
fetched_at: 2026-05-15T18:34:22.492235+00:00
content_hash: "47cf9cc3ae230ca5cd08baf9cf820dd9da152e6fce7e3ed43689401e0f535433"
lang: en
caption_quality: None
raw: true
topics: []
---

# llama.cpp constantly reprocessing huge prompts with opencode/pi.dev

I’m using llama-swap with llama.cpp. I mainly use opencode + pi.dev and I’m seeing frequent massive prompt reprocessing / prefills even tho the prompts are very similar between requests. Example behavior: context grows to +50k tokens LCP similarity often shows 0.99+ but sometimes n_past suddenly falls back to ~4-5k then llama.cpp reprocesses 40k+ tokens again TTFT jumps to multiple minutes Example logs: sim_best = 0.996 restored context checkpoint ... n_tokens = 4750 prompt eval time = 222411 ms / 44016 tokens Normal reuse looks fine: prompt eval time = 473 ms / 19 tokens Current config: llama-server --ctx-size 150000 --parallel 1 --ctx-checkpoints 32 --cache-ram 2500 --cache-reuse 256 -no-kvu --no-context-shift Also seeing: cache state: 1 prompts, 4676 MiB (limits: 2500 MiB) I suspect either: cache invalidation bad KV reuse or opencode changing early prompt tokens too often. Would love to hear from others running long-context coding agents with llama.cpp and what settings helped reduce huge prompt reprocessing. &#32; submitted by &#32; /u/No_Algae1753 [link] &#32; [comments]