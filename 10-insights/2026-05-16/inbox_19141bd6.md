---
id: inbox_19141bd6
date: 2026-05-16
source_ref: "[[00-inbox/.../inbox_19141bd6]]"
title: "Now that MTP is merged... What&#39;s the best outputs you&#39;re getting on Qwen 3.6 35B on 2x3090s?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tf7auf/now_that_mtp_is_merged_whats_the_best_outputs/
source: reddit-localllama
published_at: 2026-05-16T22:19:11+00:00
fetched_at: 2026-05-18T04:11:13.962228+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reddit 使用者詢問在雙 RTX 3090 上執行 Qwen 3.6 35B 的最佳 MTP 效能。使用者報告：原先以分層方式達 1500 tok/s 提示詞與 120 tok/s 生成，MTP 測試後生成速度跌至 80 tok/s，現階段改回 CPU overflow fallback（3500 p/p、80 t/g）。徵求其他使用者在同一硬體與模型上的 MTP 實驗結果。"
key_points:
  - "雙 3090 無 MTP：1500 tok/s 提示詞、120 tok/s 生成（分層配置）"
  - "MTP 測試後退化為 80 tok/s 生成速度"
  - "尋求 club 3090 類似優化方案改善 35B 模型在 MTP 下的表現"
tags: [mtp, qwen-3.6, rtx-3090, inference-performance]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Now that MTP is merged... What's the best outputs you're getting on Qwen 3.6 35B on 2x3090s?

Reddit 使用者詢問在雙 RTX 3090 上執行 Qwen 3.6 35B 的最佳 MTP 效能。使用者報告：原先以分層方式達 1500 tok/s 提示詞與 120 tok/s 生成，MTP 測試後生成速度跌至 80 tok/s，現階段改回 CPU overflow fallback（3500 p/p、80 t/g）。徵求其他使用者在同一硬體與模型上的 MTP 實驗結果。

### 重點
- 雙 3090 無 MTP：1500 tok/s 提示詞、120 tok/s 生成（分層配置）
- MTP 測試後退化為 80 tok/s 生成速度
- 尋求 club 3090 類似優化方案改善 35B 模型在 MTP 下的表現

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tf7auf/now_that_mtp_is_merged_whats_the_best_outputs/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Now that MTP is merged... What's the best outputs you're getting on Qwen 3.6 35B on 2x3090s?

We've got great outputs for 27B via club 3090, but what about those of us who love the blazing speed of 35B on dual 3090s? I was getting 1500 p/p and 120 t/g with split layers, but MTP slowed it down to 80 t/g when I tested last week. I'm sticking with my CPU overflow fallback of 3500 p/p and 80 t/g until someone cooks up something ala the geniuses over at club 3090. What have you tried so far with the new llama.cpp MTP merge? Any big jump over your previous best build for 35B? &#32; submitted by &#32; /u/youcloudsofdoom [link] &#32; [comments]

</details>