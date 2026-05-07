---
id: inbox_a294de81
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/0114-reddit-localllama-uploaded-unsloth-qwen3-6-35b-a3b-ud-xl-m-1396]]"
title: "Uploaded Unsloth Qwen3.6-35B-A3B UD XL models with MTP grafted, here are the results"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t5r4tz/uploaded_unsloth_qwen3635ba3b_ud_xl_models_with/
source: reddit-localllama
published_at: 2026-05-06T21:51:47+00:00
fetched_at: 2026-05-07T01:29:44.813417+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "釋出 Qwen3.6-35B-A3B-MTP-GGUF 模型至 HuggingFace，嘗試將多令牌預測（MTP）最佳化移植至 35B 稀疏模型，但效果不如 27B 版本。RTX 5090 上 Q4 量化僅獲 6.4% 加速（215 → 228.83 tok/s），Q8 搭配 3090 亦只有 2.6% 提升（148.20 → 152.02 tok/s）；相比 27B 密集版本的 2-2.5 倍加速落差明顯。另一用戶在 2x RTX 5070 Ti + 3090 上報告 110 → 165 tok/s，暗示效果可能因硬體配置不同。"
key_points:
  - "Qwen3.6-35B-A3B-MTP 在 RTX 5090 上僅達 6.4% 性能提升（Q4），遠低於 27B 版本的 2-2.5 倍"
  - "Q8 模式下雙卡配置 (5090+3090) 達 2.6% 提升，但在其他硬體組合（5070 Ti×2+3090）達 1.5 倍加速，暗示硬體與模型架構存在交互作用"
  - "模型為 MoE（混合專家）架構（35B-A3B 版本），MTP 與此類結構的相容性可能不如密集模型"
tags: [qwen3.6, mtp, moe-model, quantization, model-release]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Uploaded Unsloth Qwen3.6-35B-A3B UD XL models with MTP grafted, here are the results

釋出 Qwen3.6-35B-A3B-MTP-GGUF 模型至 HuggingFace，嘗試將多令牌預測（MTP）最佳化移植至 35B 稀疏模型，但效果不如 27B 版本。RTX 5090 上 Q4 量化僅獲 6.4% 加速（215 → 228.83 tok/s），Q8 搭配 3090 亦只有 2.6% 提升（148.20 → 152.02 tok/s）；相比 27B 密集版本的 2-2.5 倍加速落差明顯。另一用戶在 2x RTX 5070 Ti + 3090 上報告 110 → 165 tok/s，暗示效果可能因硬體配置不同。

### 重點
- Qwen3.6-35B-A3B-MTP 在 RTX 5090 上僅達 6.4% 性能提升（Q4），遠低於 27B 版本的 2-2.5 倍
- Q8 模式下雙卡配置 (5090+3090) 達 2.6% 提升，但在其他硬體組合（5070 Ti×2+3090）達 1.5 倍加速，暗示硬體與模型架構存在交互作用
- 模型為 MoE（混合專家）架構（35B-A3B 版本），MTP 與此類結構的相容性可能不如密集模型

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t5r4tz/uploaded_unsloth_qwen3635ba3b_ud_xl_models_with/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Following my previous post <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5ageq">https://www.reddit.com/r/LocalLLaMA/comments/1t5ageq</a>, a few people asked for the 35B A3B version.</p> <p>The model is up on HuggingFace at <a href="https://huggingface.co/havenoammo/Qwen3.6-35B-A3B-MTP-GGUF">https://huggingface.co/havenoammo/Qwen3.6-35B-A3B-MTP-GGUF</a> if anyone wants to check it out. It includes the isolated MTP layers and convert.py as well.</p> <p>The results are not great though. Q4 only got a 6% speed increase and Q8 only 2.5%. On the 27B it was a 2-2.5x gain, so this could be related to the MTP implementation of llama.cpp and the qwen35moe architecture or just a limitation of the model. Results are preliminary and might change in future. Either way, wanted to report back for anyone who was wondering.</p> <hr /> <p><strong>Edit:</strong> <a href="https://www.reddit.com/u/AdamDhahabi">u/AdamDhahabi</a> reported:</p> <blockquote> <p>2x 5070 Ti + 3090: Q8 went from 110 t/s to 165 t/s. 27B dense model runs at 2-2.5x speed.</p> </blockquote> <p>So the gain might depend on your setup. Worth giving it a try!</p> <hr /> <p>Here is my own tests:</p> <p>Tested with the prompt <code>hello can you tell me a story</code> on Q4.</p> <p><strong>Hardware: 5090 FE</strong></p> <p>Without MTP: 215 t/s <code> prompt eval time = 24.12 ms / 17 tokens ( 1.42 ms per token, 704.84 tokens per second) eval time = 6872.43 ms / 1478 tokens ( 4.65 ms per token, 215.06 tokens per second) total time = 6896.55 ms / 1495 tokens </code></p> <p>With MTP: 228.83 t/s <code> prompt eval time = 30.08 ms / 17 tokens ( 1.77 ms per token, 565.10 tokens per second) eval time = 8552.05 ms / 1957 tokens ( 4.37 ms per token, 228.83 tokens per second) total time = 8582.13 ms / 1974 tokens draft acceptance rate = 0.61434 ( 1268 accepted / 2064 generated) </code></p> <p>Same prompt on Q8.</p> <p><strong>Hardware: 5090 FE + 3090</strong></p> <p>Without MTP: 148.20 t/s <code> prompt eval time = 25.80 ms / 17 tokens ( 1.52 ms per token, 658.97 tokens per second) eval time = 11525.23 ms / 1708 tokens ( 6.75 ms per token, 148.20 tokens per second) total time = 11551.03 ms / 1725 tokens </code></p> <p>With MTP: 152.02 t/s <code> prompt eval time = 39.39 ms / 17 tokens ( 2.32 ms per token, 431.61 tokens per second) eval time = 10123.54 ms / 1539 tokens ( 6.58 ms per token, 152.02 tokens per second) total time = 10162.93 ms / 1556 tokens draft acceptance rate = 0.54754 ( 956 accepted / 1746 generated) </code></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/havenoammo"> /u/havenoammo </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5r4tz/uploaded_unsloth_qwen3635ba3b_ud_xl_models_with/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5r4tz/uploaded_unsloth_qwen3635ba3b_ud_xl_models_with/">[comments]</a></span>

</details>