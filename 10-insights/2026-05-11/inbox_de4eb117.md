---
id: inbox_de4eb117
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/1800-reddit-localllama-anyone-with-4x-5060ti-based-setups-1819]]"
title: "Anyone with 4x 5060ti based setups?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1ta7p6e/anyone_with_4x_5060ti_based_setups/
source: reddit-localllama
published_at: 2026-05-11T16:04:00+00:00
fetched_at: 2026-05-11T18:15:58.161392+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶討論 4× RTX 5060 Ti GPU 組態與 dual RTX 3090 在本地推理的效能對比，涉及頻寬、TFLOPs 和張量平行化的考量。RTX 5060 Ti 16GB 組態成本約 €960（相當於二手單張 RTX 3090），超頻記憶體可達 +3000MHz 達約 500GB/s 頻寬。"
key_points:
  - "RTX 5060 Ti 16GB × 4（約 €960）vs. 雙 RTX 3090（約 €1000）的成本與效能權衡"
  - "RTX 5060 Ti 超頻記憶體達 +3000MHz，頻寬可達 ~500GB/s"
  - "張量平行化在多 GPU 組態中非完全線性擴展，實際效能需實測驗證"
tags: [gpu-hardware, inference, tensor-parallelism, local-llm]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Anyone with 4x 5060ti based setups?

用戶討論 4× RTX 5060 Ti GPU 組態與 dual RTX 3090 在本地推理的效能對比，涉及頻寬、TFLOPs 和張量平行化的考量。RTX 5060 Ti 16GB 組態成本約 €960（相當於二手單張 RTX 3090），超頻記憶體可達 +3000MHz 達約 500GB/s 頻寬。

### 重點
- RTX 5060 Ti 16GB × 4（約 €960）vs. 雙 RTX 3090（約 €1000）的成本與效能權衡
- RTX 5060 Ti 超頻記憶體達 +3000MHz，頻寬可達 ~500GB/s
- 張量平行化在多 GPU 組態中非完全線性擴展，實際效能需實測驗證

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1ta7p6e/anyone_with_4x_5060ti_based_setups/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I am currently running 2x RTX 5060 ti and happened across some good sales for additional ones coinciding with a really good sale of a highend Z890 motherboard (replacing my B860 board) that could support quad GPUs (with 2 M.2 adapters, ending with running 1 GPU at 5.0 x8 and the rest at 5.0 x4, all via CPU lanes). 2x 5060 ti 16gb discounted is about the same price (~960€) as 1 used 3090 (most i can find are actuall ~1000€). I am wondering how such a quad 5060 setup compares to dual RTX 3090 in prefill and generation speed (on higher quality quants of Qwen 3.6 27B for example, like int8 / fp8)? RTX 5060 ti can easily OC memory (+3000Mhz), providing close to 500gb/s bandwidth, so looking at bandwidth per GB, its pretty close overall, and looking at FP8 TFLOPs the 5060 also comes out ahead. However, tensor parallelism is not exactly perfect scaling so I am curious where it ends up. &#32; submitted by &#32; /u/ziphnor [link] &#32; [comments]

</details>