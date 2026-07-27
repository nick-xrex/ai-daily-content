---
id: inbox_78cf6df0
date: 2026-07-26
source_ref: "[[00-inbox/2026-07-26/0123-medium-tag-llm-i-compared-lora-vs-dora-dora-was-slower-723e]]"
title: "I Compared LoRA vs. DoRA — DoRA Was Slower AND Less Accurate. Here’s Why."
url: https://medium.com/codetodeploy/i-compared-lora-vs-dora-dora-was-slower-and-less-accurate-heres-why-e0dd7d19627d?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-07-26T22:21:12+00:00
fetched_at: 2026-07-27T01:40:43.216884+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者在「無數據中心微調」自主學習系列第 3 週中直接對比 LoRA 和 DoRA 兩種參數高效微調方法，實驗發現 DoRA 在速度和準確度上雙雙落後於 LoRA。雖摘要未提供具體性能數字，但結論指出在資源受限環境中 LoRA 仍為更實用的選擇。"
key_points:
  - "DoRA（直向權重調整）在實驗中準確度和推理速度均低於 LoRA，推翻理論優勢預期"
  - "基於真實微調實驗而非模擬，為資源受限環境提供方法選型實據"
  - "LoRA 作為參數高效微調既有最佳實踐仍保有競爭力"
tags: [lora-dora-comparison, parameter-efficient-fine-tuning, model-adaptation, fine-tuning-methods]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## I Compared LoRA vs. DoRA — DoRA Was Slower AND Less Accurate. Here’s Why.

作者在「無數據中心微調」自主學習系列第 3 週中直接對比 LoRA 和 DoRA 兩種參數高效微調方法，實驗發現 DoRA 在速度和準確度上雙雙落後於 LoRA。雖摘要未提供具體性能數字，但結論指出在資源受限環境中 LoRA 仍為更實用的選擇。

### 重點
- DoRA（直向權重調整）在實驗中準確度和推理速度均低於 LoRA，推翻理論優勢預期
- 基於真實微調實驗而非模擬，為資源受限環境提供方法選型實據
- LoRA 作為參數高效微調既有最佳實踐仍保有競爭力

**原文：** [medium-tag-llm](https://medium.com/codetodeploy/i-compared-lora-vs-dora-dora-was-slower-and-less-accurate-heres-why-e0dd7d19627d?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

This is Week 3, Day 3 of my self-study series on fine-tuning AI models without a data center. Continue reading on CodeToDeploy »

</details>