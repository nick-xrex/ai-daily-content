---
id: inbox_da3b5f6e
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/1257-reddit-localllama-got-dflash-speculative-decoding-working-b17f]]"
title: "Got DFlash speculative decoding working on Qwen3.5-35B-A3B with an RTX 2080 SUPER 8GB"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t0r5nl/got_dflash_speculative_decoding_working_on/
source: reddit-localllama
published_at: 2026-05-01T11:49:01+00:00
fetched_at: 2026-05-01T13:34:01.728553+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者在 RTX 2080 SUPER 8GB 上成功部署 DFlash 推測解碼（llama.cpp PR #22105），結合 Qwen3.5-35B-A3B MoE 模型（24.44 GiB，Q5_K_M 量化）與 expert CPU 卸載，生成速度從基線 26.8 tok/s 提升至 35.6-35.8 tok/s，實現 33-34% 加速，token 接受率 99.3%。Draft 模型僅 267.8 MiB（Q4_K_M），完全驅駐 GPU。最優參數：-ncmoe 34、--draft-max 6。"
key_points:
  - "DFlash 推測解碼 + MoE expert CPU 卸載在 8GB VRAM 限制下實現 33-34% 生成加速（26.8→35.8 tok/s）"
  - "Draft 模型 Q4_K_M 量化僅 267.8 MiB，token 接受率 99.3%，配置參數：-ncmoe 34、--draft-max 6"
  - "詳細量化矩陣：Target KV 用 q8_0、Draft KV 同 q8_0，降低 draft 量化收益不明顯"
tags: [dflash, speculative-decoding, qwen3.5, rtx-2080-super, quantization, moe-expert-offload, llama-cpp]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Got DFlash speculative decoding working on Qwen3.5-35B-A3B with an RTX 2080 SUPER 8GB

使用者在 RTX 2080 SUPER 8GB 上成功部署 DFlash 推測解碼（llama.cpp PR #22105），結合 Qwen3.5-35B-A3B MoE 模型（24.44 GiB，Q5_K_M 量化）與 expert CPU 卸載，生成速度從基線 26.8 tok/s 提升至 35.6-35.8 tok/s，實現 33-34% 加速，token 接受率 99.3%。Draft 模型僅 267.8 MiB（Q4_K_M），完全驅駐 GPU。最優參數：-ncmoe 34、--draft-max 6。

### 重點
- DFlash 推測解碼 + MoE expert CPU 卸載在 8GB VRAM 限制下實現 33-34% 生成加速（26.8→35.8 tok/s）
- Draft 模型 Q4_K_M 量化僅 267.8 MiB，token 接受率 99.3%，配置參數：-ncmoe 34、--draft-max 6
- 詳細量化矩陣：Target KV 用 q8_0、Draft KV 同 q8_0，降低 draft 量化收益不明顯

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t0r5nl/got_dflash_speculative_decoding_working_on/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><pre><code>## Got DFlash speculative decoding working on Qwen3.5-35B-A3B with an RTX 2080 SUPER 8GB I managed to get **DFlash speculative decoding** working in llama.cpp on a pretty VRAM-limited setup. This was tested with the DFlash PR: https://github.com/ggml-org/llama.cpp/pull/22105 Build tested: ```text 67cb0d507 (8942) </code></pre> <p>Setup:</p> <pre><code>GPU: RTX 2080 SUPER 8GB Model: Qwen3.5-35B-A3B Q5_K_M Draft model: Qwen3.5-35B-A3B-DFlash Q4_K_M Backend: CUDA </code></pre> <p>The main model is a <strong>35B MoE</strong> GGUF around <strong>24.44 GiB</strong>, so obviously it does not fit in 8GB VRAM. The trick was combining <strong>MoE expert CPU offload</strong> with DFlash.</p> <h1>Baseline</h1> <p>My best normal non-DFlash run was around:</p> <pre><code>~26.8 tok/s </code></pre> <p>with roughly:</p> <pre><code>-ngl 999 -ncmoe 32 -fa 1 -ctk q8_0 -ctv q8_0 --no-mmap -t 5 </code></pre> <p><code>-ncmoe 32</code> was the best baseline point. Lower values used too much VRAM / performed worse, and higher values slowly reduced speed.</p> <h1>DFlash setup</h1> <p>For DFlash, I used:</p> <pre><code>Target model: C:\models\Qwen3.5-35B-A3B-Q5_K_M.gguf Draft model: C:\models\Qwen3.5-35B-A3B-DFlash-Q4_K_M.gguf </code></pre> <p>The draft model is tiny compared to the target:</p> <pre><code>DFlash draft size: ~267.8 MiB Draft params: ~474M Draft quant: Q4_K_M </code></pre> <p>Because the DFlash draft also needs VRAM, the best <code>-ncmoe</code> setting changed slightly. For the normal run, <code>-ncmoe 32</code> was best. With DFlash, the sweet spot became:</p> <pre><code>-ncmoe 34 </code></pre> <h1>Final command</h1> <p>This is the command I ended up using for testing:</p> <pre><code>build\bin\Release\llama-speculative-simple.exe ^ -m &quot;C:\models\Qwen3.5-35B-A3B-Q5_K_M.gguf&quot; ^ -md &quot;C:\models\Qwen3.5-35B-A3B-DFlash-Q4_K_M.gguf&quot; ^ --dflash ^ -p &quot;Write a complete Python implementation of quicksort, mergesort, heapsort, and binary search. Include concise comments. Write code only.&quot; ^ -n 512 ^ --draft-max 6 ^ -cd 512 -c 4096 ^ --temp 0 --top-k 1 --seed 42 ^ -ngl 999 -ngld 99 -ncmoe 34 ^ -fa on ^ -ctk q8_0 -ctv q8_0 ^ -ctkd q8_0 -ctvd q8_0 ^ --no-mmap ^ -t 5 </code></pre> <h1>Results</h1> <p>Typical DFlash result:</p> <pre><code>encoded 39 tokens in ~1.0 sec decoded 514 tokens in ~14.3-14.5 sec speed: ~35.6-35.8 tok/s n_draft = 6 n_predict = 514 n_drafted = 430 n_accept = 427 accept = 99.302% </code></pre> <p>Compared to the baseline:</p> <pre><code>Normal: ~26.8 tok/s DFlash: ~35.6-35.8 tok/s Gain: ~1.33x </code></pre> <p>So this gave me around a <strong>33–34% generation speedup</strong> on an 8GB RTX 2080 SUPER.</p> <h1>Draft length tuning</h1> <p>I tested a few <code>--draft-max</code> values:</p> <pre><code>draft-max 5: ~34.6 tok/s, accept ~97.9% draft-max 6: ~35.6-36.9 tok/s, accept ~99.3% draft-max 7: ~35.7 tok/s, accept ~95.8% draft-max 8: ~34.1 tok/s, accept ~94.7% draft-max 12: ~31.5 tok/s, accept ~83.4% </code></pre> <p><code>--draft-max 6</code> was the sweet spot. Higher values were not better because the acceptance rate dropped.</p> <h1>Quantization used</h1> <p>Target model:</p> <pre><code>Qwen3.5-35B-A3B-Q5_K_M.gguf file size: 24.44 GiB type: Q5_K_M </code></pre> <p>Internally the target GGUF reports:</p> <pre><code>f32: 301 tensors q8_0: 312 tensors q5_K: 80 tensors q6_K: 40 tensors </code></pre> <p>DFlash draft model:</p> <pre><code>Qwen3.5-35B-A3B-DFlash-Q4_K_M.gguf file size: 267.80 MiB type: Q4_K_M </code></pre> <p>Internally the draft GGUF reports:</p> <pre><code>f32: 34 tensors q4_K: 49 tensors q6_K: 8 tensors </code></pre> <p>KV cache:</p> <pre><code>Target KV: q8_0 / q8_0 Draft KV: q8_0 / q8_0 </code></pre> <p>I also tried lower draft KV quantization, but it did not really help:</p> <pre><code>draft KV q8_0/q8_0: ~35.8 tok/s draft KV q4_0/q4_0: ~35.6 tok/s </code></pre> <p>So I kept draft KV at <code>q8_0</code>.</p> <h1>Notes / caveats</h1> <p>The PR/build I tested has some weird timing output in the perf summary, including negative total time and odd unaccounted memory values.</p> <p>Because of that, I ignored those broken summary fields and focused on the stable parts:</p> <pre><code>decoded tokens / seconds accept rate n_draft / n_accept </code></pre> <p>The generated text also shows that DFlash was actually being used:</p> <pre><code>n_draft = 6 n_drafted = 430 n_accept = 427 accept = 99.302% </code></pre> <p>Also, the draft model was fully loaded on the GPU:</p> <pre><code>DFlash draft model buffer size = ~267.80 MiB offloaded 9/9 layers to GPU </code></pre> <h1>Bottom line</h1> <p>DFlash actually helped quite a bit here.</p> <p>On my setup:</p> <pre><code>RTX 2080 SUPER 8GB Qwen3.5-35B-A3B Q5_K_M DFlash draft Q4_K_M MoE CPU offload llama.cpp PR #22105 </code></pre> <p>I went from about:</p> <pre><code>26.8 tok/s </code></pre> <p>to about:</p> <pre><code>35.6-35.8 tok/s </code></pre> <p>Best current settings:</p> <pre><code>-ncmoe 34 --draft-max 6 -fa on -ctk q8_0 -ctv q8_0 -ctkd q8_0 -ctvd q8_0 --no-mmap -t 5 </code></pre> <p>Pretty happy with this result, especially considering the GPU only has 8GB VRAM.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/jwestra"> /u/jwestra </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t0r5nl/got_dflash_speculative_decoding_working_on/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t0r5nl/got_dflash_speculative_decoding_working_on/">[comments]</a></span>

</details>