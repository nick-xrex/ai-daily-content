---
id: inbox_a1f812e5
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tdty58/2_old_rtx_2080_ti_with_22gb_vram_each_qwen36_27b/"
author: "/u/snapo84"
published_at: 2026-05-15T11:48:52+00:00
fetched_at: 2026-05-15T18:34:22.490342+00:00
content_hash: "be6c188b9b72c7192bf2559abeb8bb5c2360d398dad2d0cce51bac1650b913a6"
lang: en
caption_quality: None
raw: true
topics: []
---

# 2 old RTX 2080 Ti with 22GB vram each Qwen3.6 27B at 38 token/s with f16 kv cache

PLEASE KEEP IN MIND BOTH OF MY CARDS ARE POWER LIMITED TO 150W (i hate noise) ------- Just wanted to share my current setup, that might help some users out there... services: llama-server: image: ghcr.io/ggml-org/llama.cpp:full-cuda12-b9128 container_name: llama-server restart: unless-stopped ports: - &quot;16384:8080&quot; volumes: - ./models:/models:ro command: &gt; --server --model /models/Qwen3.6-27B-IQ4_XS-uc.gguf --alias &quot;Qwen3.6 27B&quot; --temp 0.6 --top-p 0.95 --min-p 0.00 --top-k 20 --port 8080 --host 0.0.0.0 --cache-type-k f16 --cache-type-v f16 --fit on --presence-penalty 1.32 --repeat-penalty 1.0 --jinja --chat-template-file /models/Qwen3.6.jinja --mmproj /models/Qwen3.6-27B-mmproj-BF16.gguf --webui --spec-default --chat-template-kwargs '{&quot;preserve_thinking&quot;: true}' --reasoning-budget 8192 --reasoning-budget-message &quot;... thinking budget exceeded, let's answer now.\n&quot; --split-mode tensor user: &quot;1000:1000&quot; deploy: resources: reservations: devices: - driver: nvidia count: all capabilities: [gpu] environment: - NVIDIA_VISIBLE_DEVICES=all This is my exact config, my 2 extremely old 2080Ti gpus where upgraded in china to have 22GB vram each... and on ebay i bought a NVLINK (i do not recommend bying it, as no meassurable difference appears) Quantisation i run is IQ4_XS if i change the kv cache to q8_0 it sometimes happens during long coding sessions that the model loops, this is why i run kv-cache@f16 and never have this problem since then. i use the hauhaucs qwen3.6 model uncensored on IQ4 matrix quants. You can also forget about MTP as you are compute bound with those cards and not bandwidth bound. The absolut biggest boost came from --split-mode tensor , this gave me a boost from 14 token/s to 38t/s i think without the power limit we should get 45 token/s what i also never did think about is the --fit on ... i always declared context length manually worked great but it looks like its not a good idea to always run at 95% vram consumption. fit on also improved token gen a little. Btw. this is a &lt; 1k USD setup running on 400w peak on the wall, and it works great with hermes and opencode. the jinja template i use is this one: https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates (in this setup template 11, i did not yet test the newer templates) https://preview.redd.it/gasb8yo8ga1h1.png?width=476&amp;format=png&amp;auto=webp&amp;s=0450efcae279b0bcbd33f9d6d4f7241d8e3581d4 &#32; submitted by &#32; /u/snapo84 [link] &#32; [comments]