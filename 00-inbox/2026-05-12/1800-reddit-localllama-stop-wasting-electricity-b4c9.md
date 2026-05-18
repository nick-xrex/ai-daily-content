---
id: inbox_4e336d6b
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tayu5t/stop_wasting_electricity/"
author: "/u/OkFly3388"
published_at: 2026-05-12T11:32:23+00:00
fetched_at: 2026-05-12T18:00:40.878590+00:00
content_hash: "b4c98eec6d586775fea247d9f0d533f79a787b8cdb48fc6c3866ede179a38e68"
lang: en
caption_quality: None
raw: true
topics: []
---

# Stop wasting electricity

Run on my rtx4090 llama.cpp params: llama-server -m ~/Projects/llm/models/Qwen3.6-27B-UD-Q4_K_XL.gguf --flash-attn on -ngl all -ctk q4_0 -ctv q4_0 -t 32 -c 262144 Power limit was set using sudo nvidia-smi -pl N On my observation, GPU constantly hitting power limit, so its safe to say that it actual consumption. You can cut power consumption to 40% without losing performance(and also reduce noise, heat from pc, and extend lifespan of gpu). &#32; submitted by &#32; /u/OkFly3388 [link] &#32; [comments]