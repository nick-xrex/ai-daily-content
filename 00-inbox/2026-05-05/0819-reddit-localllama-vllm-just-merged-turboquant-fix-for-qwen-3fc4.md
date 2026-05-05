---
id: inbox_40aadcea
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t3zu7u/vllm_just_merged_turboquant_fix_for_qwen_35/"
author: "/u/havenoammo"
published_at: 2026-05-05T00:30:24+00:00
fetched_at: 2026-05-05T08:19:21.005227+00:00
content_hash: "3fc4094b2a02b36938879f419dcd0e2f97a94f97217c2851419a2b9aab3368b5"
lang: en
caption_quality: None
raw: true
topics: []
---

# vLLM Just Merged TurboQuant Fix for Qwen 3.5+

<!-- SC_OFF --><div class="md"><p>Previously it was throwing a 'Not Implemented' error due to Mamba layers. Going to test it now!</p> <p><a href="https://github.com/vllm-project/vllm/pull/39931">https://github.com/vllm-project/vllm/pull/39931</a></p> <p>Edit: Works with Qwen 3.6, tested with 27B<br /> Can be used with argument;</p> <pre><code>--kv-cache-dtype turboquant_4bit_nc </code></pre> <p>Other available options;</p> <ul> <li>turboquant_k8v4</li> <li>turboquant_4bit_nc</li> <li>turboquant_k3v4_nc</li> <li>turboquant_3bit_nc</li> </ul> <p>When running with <code>--enable-chunked-prefill</code> it complained about mamba align, you just need to have more batched tokens than the value that error gives. I used 4096 to fix. <code>--max-num-batched-tokens 4096</code></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/havenoammo"> /u/havenoammo </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3zu7u/vllm_just_merged_turboquant_fix_for_qwen_35/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3zu7u/vllm_just_merged_turboquant_fix_for_qwen_35/">[comments]</a></span>