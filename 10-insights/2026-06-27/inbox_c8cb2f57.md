---
id: inbox_c8cb2f57
date: 2026-06-27
source_ref: "[[00-inbox/2026-06-27/2200-medium-tag-llm-why-tokenization-latency-can-dominate-ll-ad66]]"
title: "Why Tokenization Latency Can Dominate LLM Inference — And How Perplexity Cut It by 5×"
url: https://medium.com/@jhanvijain052003/why-tokenization-latency-can-dominate-llm-inference-and-how-perplexity-cut-it-by-5-f0bec67ebf69?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-27T21:46:46+00:00
fetched_at: 2026-06-27T22:06:52.333276+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LLM 推理優化多聚焦於 GPU 性能（核心融合等），但分詞延遲往往成為真正的性能瓶頸且常被忽視。Perplexity 通過優化分詞管道實現了 5 倍延遲加速，重新定義了推理優化的優先序——應先分析瓶頸位置，再決定優化焦點。"
key_points:
  - "Perplexity 實現分詞延遲 5× 加速，證明分詞優化是高收益任務"
  - "常見誤區：工程師聚焦 GPU 優化（kernel fusion 等），卻忽視分詞延遲常主導整體推理時間"
  - "優化策略：需先用 profiler 分析瓶頸分佈，分詞延遲高時應優先優化分詞管道"
tags: [tokenization, llm-inference, latency-optimization, bottleneck, perplexity]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Why Tokenization Latency Can Dominate LLM Inference — And How Perplexity Cut It by 5×

LLM 推理優化多聚焦於 GPU 性能（核心融合等），但分詞延遲往往成為真正的性能瓶頸且常被忽視。Perplexity 通過優化分詞管道實現了 5 倍延遲加速，重新定義了推理優化的優先序——應先分析瓶頸位置，再決定優化焦點。

### 重點
- Perplexity 實現分詞延遲 5× 加速，證明分詞優化是高收益任務
- 常見誤區：工程師聚焦 GPU 優化（kernel fusion 等），卻忽視分詞延遲常主導整體推理時間
- 優化策略：需先用 profiler 分析瓶頸分佈，分詞延遲高時應優先優化分詞管道

**原文：** [medium-tag-llm](https://medium.com/@jhanvijain052003/why-tokenization-latency-can-dominate-llm-inference-and-how-perplexity-cut-it-by-5-f0bec67ebf69?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

In the race to optimize large language model (LLM) inference, most engineers instinctively focus on GPU performance &#x2014; kernel fusion&#x2026; Continue reading on Medium »

</details>