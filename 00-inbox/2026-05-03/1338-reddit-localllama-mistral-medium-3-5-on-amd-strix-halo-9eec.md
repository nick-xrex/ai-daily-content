---
id: inbox_6f95afb1
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t2twu1/mistral_medium_35_on_amd_strix_halo/"
author: "/u/Zc5Gwu"
published_at: 2026-05-03T18:49:14+00:00
fetched_at: 2026-05-04T13:38:38.126317+00:00
content_hash: "9eecdbb376f2259939c3f0dc33e79d944ac04e94440d634e24d2922d37cf4480"
lang: en
caption_quality: None
raw: true
topics: []
---

# Mistral Medium 3.5 on AMD Strix Halo

<!-- SC_OFF --><div class="md"><p>TLDR; it's slow as heck. Run overnight.</p> <p>I asked it a question about codebase architecture.</p> <p>For an end-to-end prompt of 48k tokens + 4k thinking tokens, it took about 2 hours.</p> <pre><code>llama-server -hf unsloth/Mistral-Medium-3. 5-128B-GGUF:UD-Q5_K_XL --temp 0.7 --host 0.0.0.0 --port 8080 -c 80000 -fa on -ngl 999 --no-context-shift -fit off --no-mmap -np 1 --mlock --cache-reuse 256 --chat-template-kwargs '{&quot;reasoning_effort&quot;:&quot;high&quot;}' --no-mmproj May 03 13:27:09 llama-server[6051]: prompt eval time = 4955501.32 ms / 48349 tokens ( 102.49 ms per token, 9.76 tokens per second) May 03 13:27:09 llama-server[6051]: eval time = 2652689.61 ms / 5583 tokens ( 475.14 ms per token, 2.10 tokens per second) </code></pre> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Zc5Gwu"> /u/Zc5Gwu </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2twu1/mistral_medium_35_on_amd_strix_halo/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2twu1/mistral_medium_35_on_amd_strix_halo/">[comments]</a></span>