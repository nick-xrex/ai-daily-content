---
id: inbox_5f878478
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t2zapy/pushing_a_5yearold_6gb_vram_laptop_to_its_limits/"
author: "/u/abhinand05"
published_at: 2026-05-03T22:16:02+00:00
fetched_at: 2026-05-04T13:38:38.111060+00:00
content_hash: "7147796e2284d548b0a9dc899a40c220a130d86bf941125e03beb8cb9c216255"
lang: en
caption_quality: None
raw: true
topics: []
---

# Pushing a 5-Year-Old 6GB VRAM laptop to Its Limits: Qwen3.6-35B-A3B

<!-- SC_OFF --><div class="md"><p>For the past few weeks, I have been trying to get this model working on my hardware. It still feels incredible how much better open models have become. I couldn't have gotten this model to work on my 5yo laptop if not for this sub and its amazing people. The model is actually usable at ~23 t/s...even getting 10+ t/s when unplugged! It is very good to use with pi agent. </p> <p>If you think this setup can be improved, I'd love to know more...</p> <p>I've documented my full localmaxxing journey on my blog post <a href="https://abhinandb.com/#/post/running-qwen-3-6-on-6gb-vram">here</a>, someone might find it helpful.</p> <p><strong>TL;DR</strong></p> <p>Laptop: Asus ROG Zephyrus G14 2020</p> <p>CPU: Ryzen 7 (8c 16t) @ 2900 Mhz (boost disabled)</p> <p>Mem: 24GB DDR4-3200 RAM</p> <p>GPU: RTX 2060 Max-Q 6GB VRAM</p> <p><strong>General:</strong></p> <pre><code>#!/bin/bash llama-server \ -m ~/dev/models/Qwen3.6-35B-A3B-APEX-GGUF/Qwen3.6-35B-A3B-APEX-I-Compact.gguf \ -mm ~/dev/models/Qwen3.6-35B-A3B-GGUF/mmproj-F16.gguf \ --no-mmproj-offload \ -a Qwen3.6-35B-A3B-APEX-64k \ --host 0.0.0.0 --port 8000 \ --fit off -fa on \ --ctx-size 65536 \ --threads 8 --threads-batch 12 \ --cpu-range 0-7 --cpu-strict 1 \ --cpu-range-batch 0-11 --cpu-strict-batch 1 \ --numa isolate \ --prio 2 \ --no-mmap --parallel 1 --jinja \ --cache-type-k q8_0 --cache-type-v q8_0 \ --ubatch-size 1024 --batch-size 2048 \ --n-cpu-moe 36 \ --cache-reuse 256 \ --ctx-checkpoints 8 \ --metrics \ --cache-ram 4096 \ --spec-type ngram-mod \ --spec-ngram-mod-n-match 24 --spec-ngram-mod-n-min 12 --spec-ngram-mod-n-max 48 </code></pre> <p><strong>Long Context: (Tom's fork)</strong></p> <pre><code>#!/bin/bash lm-server-tq \ -m ~/dev/models/Qwen3.6-35B-A3B-APEX-GGUF/Qwen3.6-35B-A3B-APEX-I-Compact.gguf \ -a Qwen3.6-35B-A3B-APEX-128k \ --host 0.0.0.0 --port 8000 \ --fit off -fa on \ --ctx-size 131072 \ --threads 8 --threads-batch 12 \ --cpu-range 0-7 --cpu-strict 1 \ --cpu-range-batch 0-11 --cpu-strict-batch 1 \ --numa isolate \ --prio 2 \ --no-mmap --parallel 1 --jinja \ --cache-type-k turbo3 --cache-type-v turbo4 \ --ubatch-size 1024 --batch-size 2048 \ --n-cpu-moe 36 \ --cache-reuse 256 \ --ctx-checkpoints 8 \ --metrics \ --cache-ram 4096 \ --spec-type ngram-mod \ --spec-ngram-mod-n-match 24 --spec-ngram-mod-n-min 12 --spec-ngram-mod-n-max 48 </code></pre> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/abhinand05"> /u/abhinand05 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2zapy/pushing_a_5yearold_6gb_vram_laptop_to_its_limits/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2zapy/pushing_a_5yearold_6gb_vram_laptop_to_its_limits/">[comments]</a></span>