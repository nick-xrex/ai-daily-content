---
id: inbox_578464d6
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1ta0pws/why_is_opencode_so_slow_in_processing_the_prompt/"
author: "/u/BitGreen1270"
published_at: 2026-05-11T11:40:12+00:00
fetched_at: 2026-05-12T01:13:59.606886+00:00
content_hash: "fa6aeabba997b23b1b0cbd3df5ef705d4374195045d64a4065d36df6374e5609"
lang: en
caption_quality: None
raw: true
topics: []
---

# Why is opencode so slow in processing the prompt with llama server?

I'm running opencode and llama-server locally. I have 32gb ram and 780m igpu. With Qwen3.6 I get around 21 t/s. Which should be decent but opencode just takes too long to process every input. What is it doing exactly? Tmux shows the available ram at the bottom (8+ GB available). Server startup command below the video. Once it start thinking everything goes fine. https://reddit.com/link/1ta0pws/video/4r3b899svh0h1/player ./llama-server \ -m models/Qwen3.6-35B-A3B-UD-Q3_K_S.gguf \ --temp 0.6 \ --top_p 0.95 \ --top_k 20 \ --min_p 0.0 \ --presence_penalty 0.0 \ --repeat_penalty 1.0 \ -c 65536 \ -ctk q8_0 \ -ctv q8_0 \ --flash-attn on \ -t 16 \ -ngl 99 \ --mlock \ --host 0.0.0.0 EDIT: Tried pi.dev and it definitely seems like it's related to the system prompt. pi.dev is definitely faster, probably because of the smaller system prompt. https://reddit.com/link/1ta0pws/video/nt1tpf9x7i0h1/player &#32; submitted by &#32; /u/BitGreen1270 [link] &#32; [comments]