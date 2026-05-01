---
id: inbox_3dd182ad
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-localllama-12gb-club-4070s-qwen3-6-27b-35b-a3b-and-ceca]]"
title: "12GB-Club: 4070S qwen3.6 27b + 35b a3b, and Gemma 4 26b a4b + 31b speeds"
url: https://www.reddit.com/r/LocalLLaMA/comments/1szziv0/12gbclub_4070s_qwen36_27b_35b_a3b_and_gemma_4_26b/
source: reddit-localllama
published_at: 2026-04-30T15:29:40+00:00
fetched_at: 2026-05-01T13:33:00.724367+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶在 RTX 4070S（12GB）與 AMD 9800X3D 組合上測試多個開源模型的本地推理速度。Qwen3.6-35B-A3B Q6_K_XL 達 40 token/s，Gemma 4 26B 達 26 token/s。配置支持 131K 上下文、推理模式（reasoning budget 8096–8192）、Flash Attention，附詳細 llama.cpp 配置參數，適合本地編碼代理工作流。"
key_points:
  - "Qwen3.6-35B-A3B Q6_K_XL：40 token/s；Gemma 4 26B Q8：26 token/s"
  - "支持 131K 上下文、推理預算機制（8096–8192 token）、Flash Attention"
  - "詳細 llama.cpp 配置參數公開：batch-size 4096、ubatch-size 4096、cache-type-k/v 量化"
tags: [qwen3.6, rtx-4070s, local-inference, benchmark]
topics: []
importance: 2
novelty: 1
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## 12GB-Club: 4070S qwen3.6 27b + 35b a3b, and Gemma 4 26b a4b + 31b speeds

用戶在 RTX 4070S（12GB）與 AMD 9800X3D 組合上測試多個開源模型的本地推理速度。Qwen3.6-35B-A3B Q6_K_XL 達 40 token/s，Gemma 4 26B 達 26 token/s。配置支持 131K 上下文、推理模式（reasoning budget 8096–8192）、Flash Attention，附詳細 llama.cpp 配置參數，適合本地編碼代理工作流。

### 重點
- Qwen3.6-35B-A3B Q6_K_XL：40 token/s；Gemma 4 26B Q8：26 token/s
- 支持 131K 上下文、推理預算機制（8096–8192 token）、Flash Attention
- 詳細 llama.cpp 配置參數公開：batch-size 4096、ubatch-size 4096、cache-type-k/v 量化

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1szziv0/12gbclub_4070s_qwen36_27b_35b_a3b_and_gemma_4_26b/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Longtime lurker here, thought i should post my speeeeds... </p> <p>I have a RTX 4070S 12 GB Vram (+10% OC), AMD 9800x3D with 4x16 Gb DDR5 6000Mhz CL30.</p> <p>EDIT: I offload my display to my igpu btw to save some vram on the rtx dgpu. Otherwise drop 10% or so on performance.</p> <p>EDIT2: Using this with cuda 13.1</p> <p>Please dont ask me how good they can do stuff, it's all working with no tool calls issues in VS Code with Cline and KiloCode and can use subagents too. I have not looked in to pi-coding yet.</p> <p>These models for doing WebDev are very good imho, i use Qwen3.6-35B-A3B-GGUF Q6_K_XL the most :) </p> <p><strong>TL;DR:</strong> </p> <ul> <li>Unsloth: Qwen3.6-35B-A3B-GGUF Q6_K_XL -&gt; <strong>tgs 40 pps 2100</strong> </li> <li>Unsloth: Qwen3.6-27B-IQ3_XXS -&gt; <strong>tgs 16 pps 1000</strong></li> <li>Unsloth: Gemma 4 26B-A4B-it-UD-Q8 -&gt; <strong>tgs 26 pps 2150</strong> </li> <li>Unsloth: Gemma-4-31B-it-IQ3_XXS -&gt; <strong>tgs 13-16 pps 650</strong> </li> </ul> <p>Using the following (latest llama atm) llama cpp models.ini config:</p> <p>; --- Hardware ---</p> <p>n-gpu-layers = 999</p> <p>threads = 8</p> <p>threads-batch = 16</p> <p>; --- Batching ---</p> <p>batch-size = 4096</p> <p>ubatch-size = 4096</p> <p>; --- Context ---</p> <p>ctx-size = 65536</p> <p>; --- KV Cache ---</p> <p>cache-ram = 2048</p> <p>; --- Server ---</p> <p>parallel = 1</p> <p>kv-unified = true</p> <p>flash-attn = true</p> <p>no-mmproj-offload = true</p> <p>;no-mmap = true</p> <p>; --- Sampling defaults ---</p> <p>temp = 1.0</p> <p>top-k = 40</p> <p>top-p = 0.95</p> <p>min-p = 0.01</p> <p>repeat-penalty = 1.05</p> <p>seed = 3407 </p> <p>; ==============================================</p> <p>; Unsloth Qwen3.6-35B-A3B-GGUF Q6_K_XL tgs 40 pps 2100 </p> <p>; ==============================================</p> <p>[Qwen3.6-35B-A3B-Q6_K_XL-Unsloth]</p> <p>model = E:\Apps\Ai Models\unsloth\Qwen3.6-35B-A3B-GGUF\Qwen3.6-35B-A3B-UD-Q6_K_XL.gguf</p> <p>mmproj = E:\Apps\Ai Models\unsloth\Qwen3.6-35B-A3B-GGUF\mmproj-F16.gguf</p> <p>ctx-size = 131072</p> <p>n-cpu-moe = 35</p> <p>;n-cpu-moe = 38</p> <p>cache-type-k = q8_0</p> <p>cache-type-v = q8_0</p> <p>no-mmap = true</p> <p>reasoning = on</p> <p>jinja = true</p> <p>chat-template-kwargs = {&quot;preserve_thinking&quot;: true}</p> <p>reasoning-budget = 8096</p> <p>reasoning-budget-message = Okay, enough thinking no more waiting. Let's just jump to it.</p> <p>temperature = 0.6</p> <p>top-p = 0.95</p> <p>top-k = 20</p> <p>min-p = 0.0</p> <p>presence-penalty = 0.0</p> <p>repeat-penalty = 1.0</p> <p>swa-full = true</p> <p>cache-reuse = 512 </p> <p>; ==============================================</p> <p>; Gemma 4 26B-A4B-it-UD-Q8 tgs 26 pps 2150 </p> <p>; ==============================================</p> <p>[Gemma-4-26B-A4B-Q8_0]</p> <p>model = E:\Apps\Ai Models\unsloth\gemma-4-26B-A4B-it-GGUF\gemma-4-26B-A4B-it-Q8_0.gguf</p> <p>mmproj = E:\Apps\Ai Models\unsloth\gemma-4-26B-A4B-it-GGUF\mmproj-F16.gguf</p> <p>ctx-size = 102400</p> <p>n-cpu-moe = 27</p> <p>cache-type-k = q8_0</p> <p>cache-type-v = q8_0</p> <p>reasoning = on</p> <p>jinja = true</p> <p>no-mmap = true</p> <p>reasoning-budget = 8192</p> <p>reasoning-budget-message = Okay, enough thinking no more waiting. Let's just jump in to it.</p> <p>temp = 1.0</p> <p>top-k = 64</p> <p>top-p = 0.95</p> <p>min-p = 0.00</p> <p>repeat-penalty = 1</p> <p>seed = 3407</p> <p>fit = on</p> <p>fit-target = 256</p> <p>fit-ctx = 32768</p> <p>; ==============================================</p> <p>; unsloth gemma-4-31B-it-IQ3_XXS tgs 13-16 pps 650 </p> <p>; ==============================================</p> <p>[Gemma-4-31B-IQ3_XXS-Unsloth]</p> <p>model = E:\Apps\Ai Models\unsloth\gemma-4-31B-it-GGUF\gemma-4-31B-it-UD-IQ3_XXS.gguf</p> <p>ctx-size = 51200</p> <p>ubatch-size = 256</p> <p>batch-size = 4096</p> <p>cache-type-k = q4_0</p> <p>cache-type-v = q4_0</p> <p>cache-reuse = 512</p> <p>; --- GPU offload (hardcoded = fit won't touch it) ---</p> <p>n-gpu-layers = 58</p> <p>no-mmap = true</p> <p>; --- fit only guards ctx-size from being reduced; NGL is already pinned ---</p> <p>fit = on</p> <p>fit-target = 256</p> <p>fit-ctx = 32768</p> <p>; --- Reasoning / Thinking ---</p> <p>reasoning = on</p> <p>jinja = true</p> <p>;chat-template-kwargs = {&quot;preserve_thinking&quot;: true}</p> <p>reasoning-budget = 8192</p> <p>reasoning-budget-message = Okay, enough thinking no more waiting. Let's just jump in to it.</p> <p>; --- Sampling ---</p> <p>temperature = 0.6</p> <p>top-p = 0.95</p> <p>top-k = 20</p> <p>min-p = 0.0</p> <p>presence-penalty = 0.0</p> <p>repeat-penalty = 1.0</p> <p>; --- Speculative decoding (ngram-mod) ---</p> <p>spec-type = ngram-mod</p> <p>spec-ngram-mod-n-match = 24</p> <p>spec-draft-n-min = 5</p> <p>spec-draft-n-max = 64</p> <p>no-kv-offload = true</p> <p>; ==============================================</p> <p>; Qwen3.6-27B-IQ3_XXS-Unsloth tgs 16 pps 1000</p> <p>; ==============================================</p> <p>[Qwen3.6-27B-IQ3_XXS-Unsloth]</p> <p>model = E:\Apps\Ai Models\unsloth\Qwen3.6-27B-GGUF\Qwen3.6-27B-UD-IQ3_XXS.gguf</p> <p>ubatch-size = 256</p> <p>batch-size = 4096</p> <p>cache-type-k = q4_0</p> <p>cache-type-v = q4_0</p> <p>; --- GPU offload (hardcoded = fit won't touch it) ---</p> <p>;n-gpu-layers = 63</p> <p>no-mmap = true</p> <p>; --- fit only guards ctx-size from being reduced; NGL is already pinned ---</p> <p>fit = on</p> <p>fit-target = 256</p> <p>fit-ctx = 32768</p> <p>; --- Reasoning / Thinking ---</p> <p>reasoning = on</p> <p>;grammar-file = E:\Apps\llama-cpp\grammars\think_qwen3_6.gbnf</p> <p>jinja = true</p> <p>chat-template-kwargs = {&quot;preserve_thinking&quot;: true}</p> <p>reasoning-budget = 8192</p> <p>reasoning-budget-message = Okay, enough thinking no more waiting. Let's just jump in to it.</p> <p>; --- Sampling ---</p> <p>temperature = 0.6</p> <p>top-p = 0.95</p> <p>top-k = 20</p> <p>min-p = 0.0</p> <p>presence-penalty = 0.0</p> <p>repeat-penalty = 1.0</p> <p>; --- Speculative decoding (ngram-mod) ---</p> <p>spec-type = ngram-mod</p> <p>spec-ngram-mod-n-match = 24</p> <p>spec-draft-n-min = 5</p> <p>spec-draft-n-max = 32</p> <p>no-kv-offload = true</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/mr_Owner"> /u/mr_Owner </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1szziv0/12gbclub_4070s_qwen36_27b_35b_a3b_and_gemma_4_26b/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1szziv0/12gbclub_4070s_qwen36_27b_35b_a3b_and_gemma_4_26b/">[comments]</a></span>

</details>