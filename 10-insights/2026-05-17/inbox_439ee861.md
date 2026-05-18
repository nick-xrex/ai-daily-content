---
id: inbox_439ee861
date: 2026-05-17
source_ref: "[[00-inbox/2026-05-17/0308-reddit-localllama-any-good-moe-60b-models-i-have-64gb-vram-c78e]]"
title: "Any good MOE ~60B models? I have 64GB vram"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tfzmpq/any_good_moe_60b_models_i_have_64gb_vram/
source: reddit-localllama
published_at: 2026-05-17T19:43:14+00:00
fetched_at: 2026-05-18T03:16:03.420479+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "社群提問：使用者配置 2×MI50 (32GB) 與 64GB DDR4，當前執行 Gemma 4 31B (Q4 量化)，感覺處理速度緩慢、VRAM 未充分利用。尋求 ~60B 參數規模的 MOE 模型建議，主要用途為創意寫作。該提問反映中階硬體配置面臨的模型選擇困局。"
key_points:
  - "64GB VRAM 配置尋求 ~60B MOE 模型推薦"
  - "當前 Gemma 4 31B Q4 提示處理與 token/s 速度不足"
  - "主要應用場景為創意寫作，需提升吞吐量"
tags: [moe-models, hardware-sizing, model-selection]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Any good MOE ~60B models? I have 64GB vram

社群提問：使用者配置 2×MI50 (32GB) 與 64GB DDR4，當前執行 Gemma 4 31B (Q4 量化)，感覺處理速度緩慢、VRAM 未充分利用。尋求 ~60B 參數規模的 MOE 模型建議，主要用途為創意寫作。該提問反映中階硬體配置面臨的模型選擇困局。

### 重點
- 64GB VRAM 配置尋求 ~60B MOE 模型推薦
- 當前 Gemma 4 31B Q4 提示處理與 token/s 速度不足
- 主要應用場景為創意寫作，需提升吞吐量

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tfzmpq/any_good_moe_60b_models_i_have_64gb_vram/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I have a build with 2 x MI50 32GBs and 64 gigs of DDR4 (bought before rampocolypse for ~630 USD total, I’m not rich) and I’m not gonna upgrade it for a long while. Are there any good MOE models that are around 60B in parameters so I can make use of all the VRAM? I feel like I’m stuck in a weird spot where using small models fees like a waste but I can’t really use larger models. I’ve been liking Gemma 4 31B at q4 quantisation but it’s a bit slow at both prompt processing and tps. I use it almost just for creative writing. Any suggestions? Thanks &#32; submitted by &#32; /u/opoot_ [link] &#32; [comments]

</details>