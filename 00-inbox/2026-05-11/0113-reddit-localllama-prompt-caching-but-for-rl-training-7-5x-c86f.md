---
id: inbox_49cfc2c1
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tage06/prompt_caching_but_for_rl_training_75x_speedup_on/"
author: "/u/girishkumama"
published_at: 2026-05-11T21:01:45+00:00
fetched_at: 2026-05-12T01:13:59.604101+00:00
content_hash: "c86f50b0ef02f05c95f30ed80de0e58cd9ab18e518ce16a657d1e1437f65ddbe"
lang: en
caption_quality: None
raw: true
topics: []
---

# prompt caching, but for rl training - 7.5x speedup on long-prompt/short-response workloads

most open source RL engines pack sequences naively: prompt + response, repeated for every sample in the group. this is fine for short prompt, long completion workloads but inefficient for long prompt, short completion workloads. with 1000-token prompts and 100-token responses at G=8, you're processing 8800 tokens when only 1800 are unique. about 5x wasted compute. the fix is conceptually simple: compute the prompt once, then compute all G responses after it. it's analagous to inference prefix caching, except training needs gradients to flow back through the prompt, which breaks causal attention in the obvious implementation. getting it right required different tricks for full vs. linear attention layers. you can read about it in the blogpost in the comments. Numbers on Qwen3.5-4B: - 16k prompt / 64 out → 7.5x - 16k / 128 → 7.3x - 16k / 1k → 5.4x - 8k / 4k → 1.7x &#32; submitted by &#32; /u/girishkumama [link] &#32; [comments]