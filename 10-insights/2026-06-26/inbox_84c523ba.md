---
id: inbox_84c523ba
date: 2026-06-26
source_ref: "[[00-inbox/.../inbox_84c523ba]]"
title: "Quoting OpenAI"
url: https://simonwillison.net/2026/Jun/26/openai/#atom-everything
source: simon-willison
published_at: 2026-06-26T17:10:43+00:00
fetched_at: 2026-06-29T00:59:02.340490+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 宣布推出 GPT-5.6 系列三層模型，包括旗艦級 Sol、平衡型 Terra 及經濟型 Luna，將在有限預覽後數週內全面發佈。定價策略為 Sol ($5/$30 per 1M tokens)、Terra ($2.50/$15，相比 GPT-5.5 便宜 2 倍) 及 Luna ($1/$6)。GPT-5.6 新增 prompt caching 優化，支援 explicit cache breakpoints 與 30 分鐘最短快取生命週期；cache writes 按 1.25x 標準輸入價計費，cache reads 維持 90% 折扣。此次發佈涉及美國政府預先協調，反映 AI 模型發布程序的政策監管化趨勢。"
key_points:
  - "三層分化定價：Terra 性能平衡但成本降 50%，Luna 為 $1/$6 最經濟選項，Sol 維持高端性能 $5/$30"
  - "新 cache 機制支援 explicit breakpoints 與 30 分鐘最短生命週期，cache 讀取 90% 折扣、寫入 1.25x 定價，優化長上下文與批處理成本"
  - "政府協調的有限預覽流程預示 AI 模型發布已成政策事項，涉及對標 GPT-5.5 的功能驗證與合規評估"
tags: [gpt-5.6, pricing-strategy, prompt-caching, openai]
topics: [foundation_models.gpt]
importance: 5
novelty: 5
insight_quality: 4
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## Quoting OpenAI

OpenAI 宣布推出 GPT-5.6 系列三層模型，包括旗艦級 Sol、平衡型 Terra 及經濟型 Luna，將在有限預覽後數週內全面發佈。定價策略為 Sol ($5/$30 per 1M tokens)、Terra ($2.50/$15，相比 GPT-5.5 便宜 2 倍) 及 Luna ($1/$6)。GPT-5.6 新增 prompt caching 優化，支援 explicit cache breakpoints 與 30 分鐘最短快取生命週期；cache writes 按 1.25x 標準輸入價計費，cache reads 維持 90% 折扣。此次發佈涉及美國政府預先協調，反映 AI 模型發布程序的政策監管化趨勢。

### 重點
- 三層分化定價：Terra 性能平衡但成本降 50%，Luna 為 $1/$6 最經濟選項，Sol 維持高端性能 $5/$30
- 新 cache 機制支援 explicit breakpoints 與 30 分鐘最短生命週期，cache 讀取 90% 折扣、寫入 1.25x 定價，優化長上下文與批處理成本
- 政府協調的有限預覽流程預示 AI 模型發布已成政策事項，涉及對標 GPT-5.5 的功能驗證與合規評估

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/26/openai/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Quoting OpenAI

We're beginning a limited preview of the GPT‐5.6 series: Sol, our flagship model; Terra, a balanced model for everyday work; and Luna, a fast and affordable model. Terra has competitive performance to GPT‐5.5 while being 2x cheaper and Luna brings strong capability at our lowest cost. [...] 
 We believe in broad access, and we plan to make GPT‐5.6 Sol, Terra, and Luna generally available in the coming weeks. As part of our ongoing engagement with the U.S. government, we previewed our plans and the models’ capabilities ahead of today’s launch. At their request, we are starting with a limited preview for a small group of trusted partners whose participation has been shared with the government, before releasing more broadly. [...] 
 GPT‐5.6 is priced per 1M tokens across three model sizes: Sol is $5 input / $30 output; Terra is $2.50 input / $15 output; and Luna is $1 input / $6 output. GPT‐5.6 also introduces more predictable prompt caching, including support for explicit cache breakpoints and a 30-minute minimum cache life. For GPT‐5.6 and later models, cache writes are billed at 1.25x the model’s uncached input rate, while cache reads continue to receive the 90% cached-input discount. 
 &mdash; OpenAI , Previewing GPT‐5.6 Sol: a next-generation model 

 Tags: gpt , generative-ai , ai-security-research , openai , llms , llm-release , llm-pricing

</details>