---
id: inbox_9d751caf
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t1t4nw/kv_cache_quantization_ignorance_or_malice/"
author: "/u/wombweed"
published_at: 2026-05-02T15:34:22+00:00
fetched_at: 2026-05-03T01:31:38.465790+00:00
content_hash: "4e51ad759ec4235858993046fcf217d883972c91a4fd741debfd656471781811"
lang: en
caption_quality: None
raw: true
topics: []
---

# Kv cache quantization: ignorance, or malice?

<!-- SC_OFF --><div class="md"><p>I run Qwen-3.6 27B with the FP8 safetensors on vllm for long-horizon agentic coding harness workloads with high context window and concurrent sub-agents. On two 3090s that aren’t used for anything else, it seems reasonable to expect a good balance between speed and reliability. I want to bring up a particular point of contention regarding this optimization process. I have extensive software engineering background but am relatively new to this so feel free to correct me if I’m not on the right track.</p> <p>It seems like conventional wisdom is that you shouldn’t quantize kv cache. In my experience, with my specific workloads, that remains true: with kv at fp8, I see many subtle mistakes, tool calling issues, and just plain bad reasoning. The performance is dramatically higher when I pin it at 16 bit.</p> <p>So with that in mind why do I keep seeing people gesturing at this like it’s a serious solution? I guess I can see it if it’d just low stakes chatbot stuff. But why would anyone run anything serious at anything less than full sized kv? I keep seeing stuff about turboquant as well and haven’t tried it but from what I understood, it seems like it comes with an intelligence hit too.</p> <p>So am I understanding correctly?</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/wombweed"> /u/wombweed </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1t4nw/kv_cache_quantization_ignorance_or_malice/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1t4nw/kv_cache_quantization_ignorance_or_malice/">[comments]</a></span>