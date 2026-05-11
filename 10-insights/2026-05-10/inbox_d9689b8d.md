---
id: inbox_d9689b8d
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_d9689b8d]]"
title: "MTP benchmark results: the nature of the generative task dictates whether you will benefit (coding) or get slower inference (creative) from speculative inference. No other factor comes close."
url: https://www.reddit.com/r/LocalLLaMA/comments/1t9gcar/mtp_benchmark_results_the_nature_of_the/
source: reddit-localllama
published_at: 2026-05-10T19:25:50+00:00
fetched_at: 2026-05-11T02:21:09.110359+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "研究者針對 Qwen 3.6 27B 搭配 MTP (Multi-Token Prediction) 進行 300+ 項系統性基準測試，發現投機推斷的效果**完全由任務類型決定，其他變數影響微乎其微**。編程任務加速幅度最大（F16 +171%、Q8_0 +123%），創意寫作可能反而減速（Q4_K_M -9%）。根本原因是任務類型直接決定草稿 token 接受率：編程 79–89%、創意寫作僅 39–48%，相差 40 個百分點。溫度與 MTP 層量化影響皆 <5%。最佳草稿數 N=3（F16 例外 N=4）；思考模式下編程接受率從 87% 降至 73% 但仍 +94% 加速。"
key_points:
  - "投機推斷效果由**任務類型主導**（編程 +171% vs 創意 -9%，F16 模型）；溫度、MTP 層量化影響 <5%"
  - "草稿 token 接受率差異決定性能：編程 79–89% vs 創意寫作 39–48%，40 百分點落差"
  - "最優配置矩陣：Q8_0/F16 全時啟用 MTP；Q4_K_M 創意任務禁用；N=3 草稿數普遍最優；思考模式下編程接受率下降 14% 但仍顯著加速"
tags: [speculative-decoding, mtp, qwen, quantization, benchmarking]
topics: []
importance: 5
novelty: 5
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## MTP benchmark results: the nature of the generative task dictates whether you will benefit (coding) or get slower inference (creative) from speculative inference. No other factor comes close.

研究者針對 Qwen 3.6 27B 搭配 MTP (Multi-Token Prediction) 進行 300+ 項系統性基準測試，發現投機推斷的效果**完全由任務類型決定，其他變數影響微乎其微**。編程任務加速幅度最大（F16 +171%、Q8_0 +123%），創意寫作可能反而減速（Q4_K_M -9%）。根本原因是任務類型直接決定草稿 token 接受率：編程 79–89%、創意寫作僅 39–48%，相差 40 個百分點。溫度與 MTP 層量化影響皆 <5%。最佳草稿數 N=3（F16 例外 N=4）；思考模式下編程接受率從 87% 降至 73% 但仍 +94% 加速。

### 重點
- 投機推斷效果由**任務類型主導**（編程 +171% vs 創意 -9%，F16 模型）；溫度、MTP 層量化影響 <5%
- 草稿 token 接受率差異決定性能：編程 79–89% vs 創意寫作 39–48%，40 百分點落差
- 最優配置矩陣：Q8_0/F16 全時啟用 MTP；Q4_K_M 創意任務禁用；N=3 草稿數普遍最優；思考模式下編程接受率下降 14% 但仍顯著加速

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t9gcar/mtp_benchmark_results_the_nature_of_the/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# MTP benchmark results: the nature of the generative task dictates whether you will benefit (coding) or get slower inference (creative) from speculative inference. No other factor comes close.

I recently published MTP quants of Qwen 3.6 27B and I was suprised by the reports here on reddit, and on HF, of users who were experiencing worst speed with speculative inference than without. This did not match what I was seeing, but when I tried to reproduce their exact usage, it confirmed what they were experiencing. I tried to analyse the problem, made a few conjectures which later turned out to be false, and started a full blown systematical analysis, running 300+ tests and benchmarks, collecting and comparing the results of changing various parameters. This is what I found: F16 + MTP nearly triples coding tasks speed. Q4_K_M + MTP slows down creative writing. Same feature, same model, same settings, opposite results. I did not test all quant sizes, otherwise I would still be here in a few days, but restricted my self to 5 significant ones. The other parameters I varied were task type (4 types), temperature (0.0 0.3 0.7), quantisation of the MTP layer (q8 and matching the model quant). Temp and MTP quant have very little impact on the outcome. Cumulative average decode speeds with MTP compared to the baseline without MTP, varying the model quant and task type: quant base tok/s code factual analysis creative Q4_K_M 15.1 19.7 17.5 14.9 13.7 Q5_K_M 13.1 19.2 16.5 14.7 12.6 Q6_K 13.4 20.1 17.6 15.2 13.4 Q8_0 11.4 25.4 21.7 18.6 16.9 F16 6.6 17.9 14.9 12.6 11.0 The memory bandwidth dictates how much the model can benefit from speculative decoding. F16 at 51GB crawls at 6.6 tok/s because every token means dragging the full model through memory. Accepted MTP drafts skip that pass. Q4_K_M at 16GB is already fast enough that the draft overhead is barely worth it on anything less predictable than code. What controls the draft tokens acceptance rate: task acceptance examples code 79-89% writing functions, debugging, refactoring factual 62-70% definitions, translation, math proofs analysis 48-56% tradeoff breakdowns, technical comparisons creative 39-48% stories, poetry, brainstorming, roleplay 40 points from code to creative. I tried three temperatures and five quants. The numbers barely changed. 4/5 draft tokens are correct on coding task; not even 1/2 on creative tasks. Nothing else comes close to mattering as much as what you're generating. I also tested the optimal number of draft tokens for this model in all the above scenarios. 3 is the sweet spot for draft tokens. Go higher and acceptance falls faster than the extra drafts compensate. F16 is the exception: N=4 beats N=3 (17.9 vs 16.2) because at 6.6 tok/s every surviving draft token is worth the lower hit rate. use case Q4_K_M Q5_K_M Q6_K Q8_0 F16 coding 🟢 +31% 🟢 +47% 🟢 +50% 🟢 +123% 🟢 +171% factual QA 🟡 +16% 🟢 +26% 🟢 +31% 🟢 +90% 🟢 +125% analysis 🔴 -1% 🟡 +12% 🟡 +13% 🟢 +64% 🟢 +91% creative 🔴 -9% 🔴 -4% 🔴 -1% 🟢 +48% 🟢 +67% 🟢 speeds up, 🟡 marginal gain, 🔴 slowdown. Q8_0 and F16: always use speculative decoding with MTP layer. Coding tasks at any quant: keep it on. Q4_K_M (and below) creative tasks keep it off One last obervation: with thinking mode turned on for coding tasks: Q8_0 draft token acceptance drops from 87% to 73%. Still +94% speedup, just not the full +123%. Test environment: Apple Silicon M2 Max 96GB, llama.cpp manual build with the MTP PR, Qwen3.6-27B with MTP layers preserved. &#32; submitted by &#32; /u/ex-arman68 [link] &#32; [comments]

</details>