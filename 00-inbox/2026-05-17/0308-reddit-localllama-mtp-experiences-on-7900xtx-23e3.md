---
id: inbox_b8367986
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tg25fz/mtp_experiences_on_7900xtx/"
author: "/u/Combinatorilliance"
published_at: 2026-05-17T21:17:55+00:00
fetched_at: 2026-05-18T03:08:13.231625+00:00
content_hash: "23e30c7399c4e223d21e69ee7591e38d940d229da8834039d2feacacabdfa536"
lang: en
caption_quality: None
raw: true
topics: []
---

# MTP experiences on 7900xtx?

Hi! I have been using Qwen3.6 35B A3B happily the past few weeks, and I wanted to try out Qwn3.6 27B with the new fancy MTP speculative draft! These are my settings currently: llama-server \ -m $HOME/Documents/ML/Qwen3.6-27B-Q4_K_M.gguf \ -c 64000 \ -ngl 65 \ --parallel 1 \ -t 8 \ --jinja \ --host 0.0.0.0 \ --port 5566 \ --reasoning-budget 0 \ --spec-type draft-mtp --spec-draft-n-max 3; I have a 7900XTX. This llama.cpp is built with vulkan, not ROCm. I was hoping to get usable speeds with good context to upgrade from the MoE, but so far I'm not super impressed :( With these settings my VRAM is at 93% Token speed isn't unusable with these settings but it's still quite slow :( prompt eval time = 4794.47 ms / 3445 tokens ( 1.39 ms per token, 718.54 tokens per second) eval time = 38484.86 ms / 872 tokens ( 44.13 ms per token, 22.66 tokens per second) total time = 43279.33 ms / 4317 tokens Do I need to quantize my cache? Should I drop to Q3 27B? Is 27B at Q3 better than the MoE? Additionally, I was used to 128K context on the MoE, and I didn't quantize the cache. What are your settings? Edit: I did try with a q8 cache and I was able to fit the entire model in VRAM with 64k context, and my token/s is much better, at 50tok/s, which is a definitely very usable :) &#32; submitted by &#32; /u/Combinatorilliance [link] &#32; [comments]