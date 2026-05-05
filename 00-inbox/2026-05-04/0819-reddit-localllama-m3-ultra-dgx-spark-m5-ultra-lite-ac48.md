---
id: inbox_3b320354
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t3j126/m3_ultra_dgx_spark_m5_ultralite/"
author: "/u/-dysangel-"
published_at: 2026-05-04T14:17:19+00:00
fetched_at: 2026-05-05T08:19:21.038111+00:00
content_hash: "ac4878cec4d636b8a691722f6e62ac3f339180c6d760d7b3277d3f1139b72b37"
lang: en
caption_quality: None
raw: true
topics: []
---

# M3 Ultra + DGX Spark = M5 Ultra-lite?

<!-- SC_OFF --><div class="md"><p>So I saw an article recently about exo <a href="https://blog.exolabs.net/nvidia-dgx-spark/">disaggregated prefill with DGX Spark and M3 Ultra</a> - prefill on one machine and decode on another. DGX Spark apparently has 4x matmul performance over an M3 Ultra - same as the M5 Ultra should have. So I got a Spark and have been playing around with it this weekend. Here are the results I've been getting with llama.cpp:</p> <pre><code>┌──────────────┬─────────────┬───────────────┬────────────┐ │ Model │ Mac pp16384 │ Spark pp16384 │ Result │ ├──────────────┼─────────────┼───────────────┼────────────┤ │ Qwen 35B A3B │ 1574 t/s │ 2198 t/s │ Spark 1.4x │ ├──────────────┼─────────────┼───────────────┼────────────┤ │ Qwen 27B │ 340 t/s │ 778 t/s │ Spark 2.3x │ ├──────────────┼─────────────┼───────────────┼────────────┤ │ Minimax M2.7 │ 372 t/s │ 478 t/s │ Spark 1.3x │ ├──────────────┼─────────────┼───────────────┼────────────┤ │ Mistral 128B │ 72 t/s │ 198 t/s │ Spark 2.7x │ └──────────────┴─────────────┴───────────────┴────────────┘ </code></pre> <p>In the end I found exo a little overkill for this simple use case, and so I've got Claude building a more focused and direct setup just using llama.cpp kv serialisation, and some wrappers to handle passing over the kv cache.</p> <p>For anyone who's just got a Spark or thinking of getting one: the most important thing I've found so far is to set mmap=0 for llama.cpp, otherwise it massively harms both model loading time (many minutes vs like 20 seconds) and even prefill speeds.</p> <p>The Spark is <em>tiny</em> and low power. Good complement to the M3 Ultra for a neat, quiet package.</p> <p>Of course the M3 Ultra only has ~66% of the bandwidth that the M5 Ultra will have, so decode speeds will be lower - but I'm already pretty happy with M3 decode. The M5 Ultra definitely won't be enough of a boost that I'm going to drop another $10k on it. My current setup is now somewhere between an M5 Max and M5 Ultra, but with CUDA capability.</p> <p>If I upgraded anything just now, it would probably be adding a second Spark via the 200GbE!</p> <p>I wonder if I can get even better performance with vllm too, especially for batching. If anyone has good info on this, can they post in here? I'll keep experimenting and keep you guys posted if people are interested.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/-dysangel-"> /u/-dysangel- </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3j126/m3_ultra_dgx_spark_m5_ultralite/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3j126/m3_ultra_dgx_spark_m5_ultralite/">[comments]</a></span>