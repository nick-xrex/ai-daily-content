---
id: inbox_d14d815b
date: 2026-05-12
source_ref: "[[00-inbox/2026-05-12/1800-reddit-localllama-gemma-4-mtp-vs-dflash-on-1x-h100-dense-v-2c1a]]"
title: "Gemma 4 MTP vs DFlash on 1x H100: dense vs MoE results"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tb160j/gemma_4_mtp_vs_dflash_on_1x_h100_dense_vs_moe/
source: reddit-localllama
published_at: 2026-05-12T13:09:07+00:00
fetched_at: 2026-05-12T18:12:25.016793+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Gemma 4 模型在 H100 上的 speculative decoding 對比測試。測試了 MTP (Medusa Token Prediction) 和 DFlash 兩種方法，在 Gemma 4 31B dense 模型上都達到約 3x 加速（baseline 40 tok/s → MTP 125 tok/s），高並發時 MTP 953 tok/s vs DFlash 725 tok/s。Gemma 4 26B-A3B MoE 上結果反轉，DFlash 更優（306 vs 264 tok/s 在並發1）。關鍵發現：MoE 加速較小是因為 baseline 已很快（只 3.8B active params），使得 speculative decoding 收益受限；工作負載差異明顯，coding/math 類受益更多（token 更可預測），writing/summarization 類受益少。Position 越後接受率越低，位置8 已跌至 <20%。"
key_points:
  - "Dense 模型 3.11x 加速（40→125 tok/s），MoE 只 1.73x（177→306 tok/s）——MoE baseline 已快導致 speculative decoding 邊際效益遞減"
  - "Coding/STEM 類任務因 token pattern 可預測性高而加速效果好，writing/summarization 類效果差"
  - "Token 位置 1 接受率 80% (MTP) 快速跌至位置 8 的 <20%，說明預測困難度隨序列深度指數增長"
tags: [speculative-decoding, gemma-4, mtp-vs-dflash, moe-optimization, inference-benchmarking]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Gemma 4 MTP vs DFlash on 1x H100: dense vs MoE results

Gemma 4 模型在 H100 上的 speculative decoding 對比測試。測試了 MTP (Medusa Token Prediction) 和 DFlash 兩種方法，在 Gemma 4 31B dense 模型上都達到約 3x 加速（baseline 40 tok/s → MTP 125 tok/s），高並發時 MTP 953 tok/s vs DFlash 725 tok/s。Gemma 4 26B-A3B MoE 上結果反轉，DFlash 更優（306 vs 264 tok/s 在並發1）。關鍵發現：MoE 加速較小是因為 baseline 已很快（只 3.8B active params），使得 speculative decoding 收益受限；工作負載差異明顯，coding/math 類受益更多（token 更可預測），writing/summarization 類受益少。Position 越後接受率越低，位置8 已跌至 <20%。

### 重點
- Dense 模型 3.11x 加速（40→125 tok/s），MoE 只 1.73x（177→306 tok/s）——MoE baseline 已快導致 speculative decoding 邊際效益遞減
- Coding/STEM 類任務因 token pattern 可預測性高而加速效果好，writing/summarization 類效果差
- Token 位置 1 接受率 80% (MTP) 快速跌至位置 8 的 <20%，說明預測困難度隨序列深度指數增長

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tb160j/gemma_4_mtp_vs_dflash_on_1x_h100_dense_vs_moe/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Benchmarked Gemma 4 MTP and z-lab's DFlash on a single H100 80GB using vLLM and NVIDIA's SPEED-Bench qualitative dataset. Setup: Hardware: 1x H100 80GB Runtime: vLLM Dataset: SPEED-Bench qualitative Prompts: 880 total, 80 prompts across each of 11 categories Models: google/gemma-4-31B-it and google/gemma-4-26B-A4B-it MTP drafts: Google's matching Gemma 4 assistant models DFlash drafts: z-lab's matching Gemma 4 DFlash models MTP used num_speculative_tokens=8 DFlash used num_speculative_tokens=15 Context length / max model length: 32768 Temperature: 0 Prefix caching was disabled Results: For Gemma 4 31B dense, MTP was 3.11x faster and DFlash was 3.03x faster than baseline decoding at concurrency 1. Baseline hit 40.3 output tok/s, MTP hit 125.3 output tok/s, and DFlash hit 122.1 output tok/s. At concurrency 16, baseline reached 375 tok/s, MTP reached 953 tok/s, and DFlash reached 725 tok/s. https://preview.redd.it/4zyyt58j7p0h1.png?width=2571&amp;format=png&amp;auto=webp&amp;s=930d3a8383fb7fe40749217867f4f3ab9877b4a4 For Gemma 4 26B-A4B MoE , the result flipped. DFlash was 1.73x faster and MTP was 1.49x faster than baseline decoding at concurrency 1. Baseline hit 177.1 output tok/s, MTP hit 264.2 output tok/s, and DFlash hit 306.4 output tok/s. At concurrency 16, baseline reached 975 tok/s, MTP reached 1808 tok/s, and DFlash reached 1957 tok/s. The MoE speedups were smaller than the dense-model speedups because the baseline MoE target is already relatively cheap to run. Gemma 4 26B-A4B has 25.2B total parameters, but only 3.8B active parameters during inference. That means speculative decoding has less target-model compute to remove compared with the dense 31B model. https://preview.redd.it/twdqm7pk7p0h1.png?width=2596&amp;format=png&amp;auto=webp&amp;s=71b388e143bd384fec08e299b3996ba8337e42f8 The gains were not uniform across workloads. Coding, math, STEM, and reasoning benefited more because these tasks often have more predictable token patterns. Writing, summarization, and roleplay improved less because there are many valid ways for the model to continue the text. Higher per-position acceptance did not automatically mean higher throughput. MTP accepted more draft tokens, but DFlash showed better throughput on the MoE model. Acceptance is only one side of it. DFlash drafts the whole block in a single forward pass, while MTP drafts token by token. When the target is this fast, the cheaper draft path can matter more even with lower acceptance. Most accepted draft tokens came from the first few positions. Position-1 acceptance was around 80% for MTP and 75% for DFlash, but by position 8 it dropped to under 20% for both. https://preview.redd.it/di8n1c3m7p0h1.png?width=2615&amp;format=png&amp;auto=webp&amp;s=e769d24d5ae9ad4722270437eef1f26a998ac6e8 For a real deployment, try both approaches on your own setup and workload instead of assuming one will always be better. The results can change with the model, prompts, hardware, and serving configuration. Hope these numbers give people a useful reference point. All the benchmark setup and scripts used for benchmarking and to reproduce these results are in the Github repository . You can read about more results and in-depth analysis in our blog: https://jarvislabs.ai/blog/gemma-4-mtp-vs-dflash-benchmark &#32; submitted by &#32; /u/LayerHot [link] &#32; [comments]

</details>