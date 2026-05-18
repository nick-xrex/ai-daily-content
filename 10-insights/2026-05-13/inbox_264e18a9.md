---
id: inbox_264e18a9
date: 2026-05-13
source_ref: "[[00-inbox/.../inbox_264e18a9]]"
title: "running Qwen 3.6 35b A3B on 2x 5060TI"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tch5ps/running_qwen_36_35b_a3b_on_2x_5060ti/
source: reddit-localllama
published_at: 2026-05-13T23:50:33+00:00
fetched_at: 2026-05-18T03:44:23.048941+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶在 2x RTX 5060Ti（總計 32GB VRAM）上運行 Qwen 3.6 35B A3B 模型，Q4 量化達 90t/s 吞吐量，全 context。提問是否有優化方案支援更高量化級別（Q6/Q8），以及 mATX 主板上雙 GPU 堆疊（無空隙）的散熱解決方案。"
key_points:
  - "Qwen 3.6 35B A3B @ Q4 on 2x RTX 5060Ti = 90t/s（全 context）"
  - "用戶尋求進一步優化空間，目標升級到 Q6/Q8 量化"
  - "實務限制：mATX 主板雙 GPU 物理堆疊散熱困難"
tags: [qwen-3.6, quantization, rtx-5060ti, inference, hardware]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## running Qwen 3.6 35b A3B on 2x 5060TI

用戶在 2x RTX 5060Ti（總計 32GB VRAM）上運行 Qwen 3.6 35B A3B 模型，Q4 量化達 90t/s 吞吐量，全 context。提問是否有優化方案支援更高量化級別（Q6/Q8），以及 mATX 主板上雙 GPU 堆疊（無空隙）的散熱解決方案。

### 重點
- Qwen 3.6 35B A3B @ Q4 on 2x RTX 5060Ti = 90t/s（全 context）
- 用戶尋求進一步優化空間，目標升級到 Q6/Q8 量化
- 實務限制：mATX 主板雙 GPU 物理堆疊散熱困難

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tch5ps/running_qwen_36_35b_a3b_on_2x_5060ti/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# running Qwen 3.6 35b A3B on 2x 5060TI

i ran Qwen 3.6 35b A3B two 5060TI 16gb ( 32 gb vram total also i have 32gb dram but i don't like offloading ) i used Q4 on LM Studio with full context and i get 90t/s any tricks to optimze this more to upgrade to Q6 or Q8 ? thanks ! another thing if you recommend somthing for cooling because i am using 2 stacked gpus with 0 gap ( i have and mATX motherboard ) now the top gpu it not that hot but hotter then the bottom one &#32; submitted by &#32; /u/chocofoxy [link] &#32; [comments]

</details>