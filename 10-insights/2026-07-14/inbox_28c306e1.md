---
id: inbox_28c306e1
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-substack-bytebytego-how-llms-learn-to-be-helpful-rlhf-vs-dpo-b3e9]]"
title: "How LLMs Learn to Be Helpful (RLHF vs DPO)"
url: https://blog.bytebytego.com/p/how-llms-learn-to-be-helpful-rlhf
source: substack-bytebytego
published_at: 2026-07-14T15:30:53+00:00
fetched_at: 2026-07-14T22:22:02.440683+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文詳解 LLM 如何習得有用行為的機制，核心是兩種主流方法的對比：RLHF（從人類回饋中強化學習）與 DPO（直接偏好最佳化）。文章首先說明為什麼單純的指令調整（instruction-following）不足以達成真正的模型對齐，然後逐步解釋 RLHF 和 DPO 的原理、優劣和應用場景。理解這兩種方法是預測模型表現和比較模型質量的關鍵知識。"
key_points:
  - "RLHF 與 DPO 是 LLM 對齐的兩種主要方法，各自有優劣和權衡"
  - "指令調整單獨不足以確保模型行為符合期望，需加入偏好學習層"
  - "理解這兩種方法對預測 LLM 行為、評估模型質量和推測未來發展至關重要"
tags: [llm-training, rlhf, dpo, model-alignment]
topics: []
importance: 4
novelty: 2
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## How LLMs Learn to Be Helpful (RLHF vs DPO)

本文詳解 LLM 如何習得有用行為的機制，核心是兩種主流方法的對比：RLHF（從人類回饋中強化學習）與 DPO（直接偏好最佳化）。文章首先說明為什麼單純的指令調整（instruction-following）不足以達成真正的模型對齐，然後逐步解釋 RLHF 和 DPO 的原理、優劣和應用場景。理解這兩種方法是預測模型表現和比較模型質量的關鍵知識。

### 重點
- RLHF 與 DPO 是 LLM 對齐的兩種主要方法，各自有優劣和權衡
- 指令調整單獨不足以確保模型行為符合期望，需加入偏好學習層
- 理解這兩種方法對預測 LLM 行為、評估模型質量和推測未來發展至關重要

**原文：** [substack-bytebytego](https://blog.bytebytego.com/p/how-llms-learn-to-be-helpful-rlhf)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

In this article, we will look at how that learning actually happens, starting with why instruction-following alone falls short, then walking through the two main methods for teaching preferences (RLHF and DPO).

</details>