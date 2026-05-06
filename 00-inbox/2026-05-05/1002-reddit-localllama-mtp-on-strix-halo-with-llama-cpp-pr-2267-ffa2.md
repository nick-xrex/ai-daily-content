---
id: inbox_b00e325f
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t4uj9h/mtp_on_strix_halo_with_llamacpp_pr_22673/"
author: "/u/Edenar"
published_at: 2026-05-05T22:26:41+00:00
fetched_at: 2026-05-06T10:02:16.878708+00:00
content_hash: "ffa2c2e7a6b85b99ca9090fc255aa3b3aabe2de5f29ea93ed4ac0d738027f1f6"
lang: en
caption_quality: None
raw: true
topics: []
---

# MTP on strix halo with llama.cpp (PR #22673)

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4uj9h/mtp_on_strix_halo_with_llamacpp_pr_22673/"> <img alt="MTP on strix halo with llama.cpp (PR #22673)" src="https://preview.redd.it/xvtyf87u6ezg1.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=8ac472eeaa0c2957b855097981b9a8c631e92fbc" title="MTP on strix halo with llama.cpp (PR #22673)" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>I saw a post about incoming MTP support in llama.cpp so i tried it out on a AI max 395 with 128GB DDR5 8000:<br /> I rebuilt the radv container from <a href="https://github.com/kyuz0/amd-strix-halo-toolboxes">https://github.com/kyuz0/amd-strix-halo-toolboxes</a> with that PR : <a href="https://github.com/ggml-org/llama.cpp/pull/22673">https://github.com/ggml-org/llama.cpp/pull/22673</a><br /> I ran that GGUF : <a href="https://huggingface.co/am17an/Qwen3.6-35BA3B-MTP-GGUF/tree/main">https://huggingface.co/am17an/Qwen3.6-35BA3B-MTP-GGUF/tree/main</a> and added <code>--spec-type mtp --spec-draft-n-max 3</code></p> <p>Result : between 60 and 80 token/s from 40ish token/s without MTP (on the screen i was trying rocm but it's more like 40-45 token/s with vulkan) depending on the subject (some common math stuff seems to be the fastest). PP seems unchanged. The two GGUF on the screen capture are almost the same size : around 36GB each</p> <p>I have yet to try it on qwen 3.5 122B and there will be some tweaks to do with launch parameters but it's really impressive !!</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Edenar"> /u/Edenar </a> <br /> <span><a href="https://i.redd.it/xvtyf87u6ezg1.png">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4uj9h/mtp_on_strix_halo_with_llamacpp_pr_22673/">[comments]</a></span> </td></tr></table>