---
id: inbox_a7a87d62
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_a7a87d62]]"
title: "Is there a big gap between Q4 and Q6 on Qwen3.6?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1td7qw0/is_there_a_big_gap_between_q4_and_q6_on_qwen36/
source: reddit-localllama
published_at: 2026-05-14T18:59:22+00:00
fetched_at: 2026-05-18T03:57:49.558704+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reddit LocalLLaMA 社群提問：單張 RTX 3090 運行 Qwen 3.6 27B Q4_M 量化達 65 tok/s，上下文 65k-100k。提問者考慮購買第二張 3090 以支持更高量化（Q5/Q6），向社群詢問量化級別差異與模型大小組合的實務影響。無具體測試數據，純社群討論。"
key_points:
  - "Qwen 3.6 27B Q4_M 在 3090 上達 65 tok/s 推理速度"
  - "提問者考慮雙 3090 以支持 Q5/Q6 量化，詢問成本效益"
  - "未提供 Q4 vs Q5 vs Q6 的對比數據"
tags: [qwen, quantization, gpu-optimization]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Is there a big gap between Q4 and Q6 on Qwen3.6?

Reddit LocalLLaMA 社群提問：單張 RTX 3090 運行 Qwen 3.6 27B Q4_M 量化達 65 tok/s，上下文 65k-100k。提問者考慮購買第二張 3090 以支持更高量化（Q5/Q6），向社群詢問量化級別差異與模型大小組合的實務影響。無具體測試數據，純社群討論。

### 重點
- Qwen 3.6 27B Q4_M 在 3090 上達 65 tok/s 推理速度
- 提問者考慮雙 3090 以支持 Q5/Q6 量化，詢問成本效益
- 未提供 Q4 vs Q5 vs Q6 的對比數據

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1td7qw0/is_there_a_big_gap_between_q4_and_q6_on_qwen36/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Is there a big gap between Q4 and Q6 on Qwen3.6?

I’ve got one 3090 and thanks to the help of MTP and all, I can do around 65 tok/s on qwen 3.6 dense 27b. But I’m running at Q4_M so everything fits and my context isn’t super high. Maybe 65k or up to 100k. I’ve thrown around the idea of a second 3090. But I do already have some gaming PCs running parallel stuff with smaller 3080 (2x) and 4080S cards to support my 3090. So it seems the real benefit of a second 3090 is running at a higher quant. But for those that do, have you noticed a big difference? Also, what about when it comes to the size of the model as in Q5_XS vs Q4_XL and so on? Would Q4 be better in that situation? &#32; submitted by &#32; /u/vick2djax [link] &#32; [comments]

</details>