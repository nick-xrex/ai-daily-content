---
id: inbox_b3636e76
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t5tnzl/get_faster_qwen_36_27b/"
author: "/u/admajic"
published_at: 2026-05-06T23:33:07+00:00
fetched_at: 2026-05-07T01:14:38.449345+00:00
content_hash: "553d65c14fd447ad926608bc6e85a4f3a4c2c82a3b1f91d808f9ce9dc6406c2c"
lang: en
caption_quality: None
raw: true
topics: []
---

# Get faster qwen 3.6 27b

<!-- SC_OFF --><div class="md"><p>Using 100k context with 3090 with MTP GGUF and getting 50 t/s on llama.cpp</p> <p>Thought I would knowledge share</p> <p>Use <a href="https://huggingface.co/RDson/Qwen3.6-27B-MTP-Q4_K_M-GGUF">https://huggingface.co/RDson/Qwen3.6-27B-MTP-Q4_K_M-GGUF</a></p> <p>And am17an commit</p> <p>/media/adam/D_DRIVE/LLM/llama-cpp-am17an/build/bin/llama-server </p> <p>-m &quot;/media/Qwen3.6-27B-Q4/Qwen3.6-27B-MTP-Q4_K_M.gguf&quot; \</p> <p>--ctx-size 100000 \</p> <p>-ngl 99 -fa on \</p> <p>--cache-type-k q4_0 --cache-type-v q4_0 \</p> <p>--batch-size 2048 --ubatch-size 1024 \</p> <p>--spec-type mtp --spec-draft-n-max 2 \</p> <p>--flash-attn</p> <p>Note: Spec draft 3 seemed to much for the 3090 at higher context</p> <p>Why 100k context? Beside it slows down and 100k is enough for most tasks then compact and continue. </p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/admajic"> /u/admajic </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5tnzl/get_faster_qwen_36_27b/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5tnzl/get_faster_qwen_36_27b/">[comments]</a></span>