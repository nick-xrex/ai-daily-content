---
id: inbox_4ba35110
date: 2026-05-17
source_ref: "[[00-inbox/.../inbox_4ba35110]]"
title: "MTP for Qwen3.6-35B-A3B on 6GB VRAM laptop: not worth it"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tfq683/mtp_for_qwen3635ba3b_on_6gb_vram_laptop_not_worth/
source: reddit-localllama
published_at: 2026-05-17T13:52:42+00:00
fetched_at: 2026-05-18T04:11:13.958137+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者在 6GB VRAM 筆電（Asus ROG Zephyrus G14 2021、RTX 3060、Ryzen 7 5800HS）上實驗 llama.cpp 新合併的 MTP（Multi-Token Prediction）功能。結論：MTP 不划算──提示詞處理速度大幅下降，抵消了微小的文字生成速度提升。具體數據：無 MTP 基線達 23–26 tok/s 生成速度，MTP 僅 81–82 tok/s，提示詞速度 176–299 tok/s 降至 138–198 tok/s。發現實用技巧：q4_0 量化用於草稿 KV 快取可節省 VRAM，效果等同 q8_0 但無質量損失。"
key_points:
  - "MTP 在 VRAM 受限情況（6GB）下提示詞速度損失過大（降低 50–54%），導致整體不划算"
  - "量化實驗：q4_0 用於草稿 KV 快取（與主要快取同樣 q8_0）節省 VRAM，草稿模型準確度無明顯下降"
  - "無 MTP baseline (ubatch 2048)：PP 400+ tok/s、TG 23–26 tok/s；MTP 最佳 (ubatch 512)：PP 25–26 tok/s、TG 81–82 tok/s（PP 大幅衰退）"
tags: [mtp, llama-cpp, quantization, kv-cache, vram-optimization, qwen-3.6]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## MTP for Qwen3.6-35B-A3B on 6GB VRAM laptop: not worth it

開發者在 6GB VRAM 筆電（Asus ROG Zephyrus G14 2021、RTX 3060、Ryzen 7 5800HS）上實驗 llama.cpp 新合併的 MTP（Multi-Token Prediction）功能。結論：MTP 不划算──提示詞處理速度大幅下降，抵消了微小的文字生成速度提升。具體數據：無 MTP 基線達 23–26 tok/s 生成速度，MTP 僅 81–82 tok/s，提示詞速度 176–299 tok/s 降至 138–198 tok/s。發現實用技巧：q4_0 量化用於草稿 KV 快取可節省 VRAM，效果等同 q8_0 但無質量損失。

### 重點
- MTP 在 VRAM 受限情況（6GB）下提示詞速度損失過大（降低 50–54%），導致整體不划算
- 量化實驗：q4_0 用於草稿 KV 快取（與主要快取同樣 q8_0）節省 VRAM，草稿模型準確度無明顯下降
- 無 MTP baseline (ubatch 2048)：PP 400+ tok/s、TG 23–26 tok/s；MTP 最佳 (ubatch 512)：PP 25–26 tok/s、TG 81–82 tok/s（PP 大幅衰退）

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tfq683/mtp_for_qwen3635ba3b_on_6gb_vram_laptop_not_worth/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# MTP for Qwen3.6-35B-A3B on 6GB VRAM laptop: not worth it

I have an Asus gaming laptop from 2021 that I bought used for 500€ last year. I wanted to see if the recently merged MTP support in llama.cpp is worth using on such a VRAM constrained device for the Qwen3.6-35B-A3B model. So I did some experiments to measure performance with and without MTP. TL;DR: It's not worth it. The prompt processing is so much slower with MTP that it outweighs the minimal gains in TG speeds. However, I did discover a useful VRAM saving trick: using q4_0 quantization for the draft KV cache works just as well as q8_0 and saves a small bit of VRAM. Hardware Asus ROG Zephyrus G14 laptop, 2021 model AMD Ryzen 7 5800HS with Radeon Graphics (8 CPU cores / 16 threads) NVIDIA RTX 3060 Laptop GPU, 6GB VRAM 24GB RAM (DDR4 3200 MT/s), 1TB SSD Software Linux Mint 22.2 (based on Ubuntu 24.04) with the Cinnamon desktop running on the Radeon iGPU (thus the 3060 was dedicated to llama.cpp only) llama.cpp version: 9198 (a6d6183db) built from current master branch with GNU 13.3.0 for Linux x86_64 CUDA 12.0 installed from Ubuntu repositories Test setup I fixed the following parameters for all the experiments: Unsloth Qwen3.6-35B-A3B-MTP-UD-Q4_K_XL model (pushing the maximum this system can run; I used the same model for both MTP and non-MTP, just varying the command line arguments so the MTP part of the model was not used in all runs) q8_0 quantization for the main KV cache (I don't want to compromise on quality too much) context size 65536 (enough to do agentic coding on e.g. Pi or Dirac, or run Hermes Agent) for MTP, I used --spec-draft-n-max 2 (I know that 3 might be slightly better in some cases, but decided to stick to this to make the results comparable) mmap enabled (it's the only way I can run this model without freezing my machine...) I varied these parameters: MTP vs non-MTP (including/omitting MTP specific CLI parameters) ubatch size: 512, 1024, 1536, 2048 draft model KV cache quantization: either q8_0 or q4_0 (always same for both K &amp; V) --fit-target set to the lowest value (in steps of 64) that works without OOM errors Here is an example of a full llama-server command (MTP 1 in the table below): build/bin/llama-server \ -m Qwen3.6-35B-A3B-MTP-UD-Q4_K_XL.gguf \ --threads 8 \ -ub 512 \ --parallel 1 \ --fit-target 448 \ -c 65536 \ -ctk q8_0 \ -ctv q8_0 \ -ctkd q8_0 \ -ctvd q8_0 \ --chat-template-kwargs '{&quot;preserve_thinking&quot;: true}' \ --temp 0.6 \ --top-p 0.95 \ --min-p 0.0 \ --top-k 20 \ --repeat-penalty 1.0 \ --presence-penalty 0.0 \ --spec-type draft-mtp \ --spec-draft-n-max 2 The tasks I gave the model were two: MB: Run the mtp-bench.py script to benchmark MTP on various different tasks. S: Summarize a longer document (MTP PR 22673 from github) into a few bullet points. This is a 13448 token prompt followed by 2000-3000 tokens of generation. Results This table summarizes the outcome. ub = ubatch size, dKV = draft KV quant type, fitt = fit-target value, acc% = acceptance rate. Setup ub dKV fitt MB TG MB acc% S PP S TG S acc% No MTP 1 512 - 0 25.0 - 178 23.8 - No MTP 2 1024 - 0 23.1 - 292 22.5 - No MTP 3 1536 - 0 24.5 - 299 24.4 - No MTP 4 2048 - 0 23.0 - 436 26.1 - MTP 1 512 q8_0 448 27.3 81.5 143 26.1 76.5 MTP 2 1024 q8_0 960 18.7 82.7 138 25.9 72.0 MTP 3 512 q4_0 448 26.4 81.5 139 25.3 73.4 MTP 4 1024 q4_0 960 25.4 82.7 198 23.7 73.7 I also tried higher ubatch values with MTP, but the results were so bad (TG 10-15 tok/s, probably due to running out of RAM and swapping) that I aborted those runs. Verdict The baseline &quot;No MTP 4&quot; with ubatch=2048 is clearly the best non-MTP setup. It reached PP speeds over 400 tok/s and TG speeds of 23-26 tok/s. The &quot;MTP 1&quot; run with ubatch=512 reached the best TG speed (over 27 tok/s) in mtp-bench but was tied with &quot;No MTP 4&quot; on the summarization task TG. PP speeds were much lower than any non-MTP setups. Increasing ubatch size in MTP can improve PP speeds a bit, especially in the &quot;MTP 4&quot; setup which also used q4_0 quantization for the draft KV cache. But this practically eliminated the benefit in TG speeds while still more than halving PP speeds. In short: MTP is not worth it in this setting. Tiny increase in TG for some cases, but always a giant drop in PP speeds. If PP speeds for MTP are later improved in llama.cpp (this was listed as a known issue in the PR), this might change. Observations I was surprised to see that using q4_0 quantization for the draft model KV cache had negligible impact on draft model accuracy. This saves a tiny bit of VRAM, so might be a useful trick for very VRAM constrained setups. There is a bit of unexplained variation between measurements, probably due to random change, CPU/GPU temperature throttling etc. Not too bad, but take with a grain of salt. VRAM is obviously very tight from the start. The MTP VRAM overhead easily pushes the system into a badly performing scenario. The --fit and --fit-target options don't seem to take into account the MTP overhead; you need to reserve some memory for MTP and this amount depends mainly on the ubatch size. Thus you have to set --fit-target manually if you want to squeeze the maximum performance out of your limited VRAM. In my case, setting fit-target to a number a bit less than the ubatch size seemed to work, but YMMV. Notes This post was constructed from 100% organic ingredients. No AIs were harmed in the process. My second post here. Happy to answer any questions. &#32; submitted by &#32; /u/OsmanthusBloom [link] &#32; [comments]

</details>