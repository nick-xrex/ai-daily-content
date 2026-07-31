---
id: inbox_f137b051
date: 2026-07-30
source_ref: "[[00-inbox/2026-07-30/0107-simon-willison-advancing-the-price-performance-frontier-a7f3]]"
title: "Advancing the price-performance frontier with GPT‐5.6"
url: https://simonwillison.net/2026/Jul/30/luna-price-drop/#atom-everything
source: simon-willison
published_at: 2026-07-30T23:58:42+00:00
fetched_at: 2026-07-31T01:12:40.838979+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 大幅降低 GPT-5.6 系列定价，其中 Terra 降价 20%，Luna 降价 80%，后者现价为 $0.20/M 输入和 $1.20/M 输出。OpenAI 利用 GPT-5.6 Sol 自主优化模型的前向传播，通过 Triton 和 Gluon 等开源 GPU 编程语言重写生产 kernels，实现端到端服务成本降低 20%。Luna 现已成为市场上最便宜的前沿竞争模型，比 Google Gemini 3.1 Flash-Lite ($0.025/$1.50) 和 Anthropic 的 Claude Haiku 4.5 ($1/$5) 都更便宜。其输入价格为 Haiku 的 1/5，使其成为成本敏感应用的新基准。这一价格变化正在改变许多开发者的模型选择，Simon Willison 已将其 agent.datasette.io 项目从 Gemini 3.1 Flash-Lite 切换至 Luna。"
key_points:
  - "GPT-5.6 Luna 价格 $0.20/M input、$1.20/M output，相比 Claude Haiku 4.5 ($1/$5) 便宜超过 80%，成为最便宜的前沿模型"
  - "OpenAI 用 GPT-5.6 Sol 通过 Triton 和 Gluon 重写生产 kernel，实现端到端服务成本降低 20%"
  - "Luna 正取代 Gemini 3.1 Flash-Lite 成为开发者成本基准，改变生态中的模型选择格局"
tags: [gpt-5-6, pricing, model-optimization, cost-reduction]
topics: [foundation_models.gpt]
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Advancing the price-performance frontier with GPT‐5.6

OpenAI 大幅降低 GPT-5.6 系列定价，其中 Terra 降价 20%，Luna 降价 80%，后者现价为 $0.20/M 输入和 $1.20/M 输出。OpenAI 利用 GPT-5.6 Sol 自主优化模型的前向传播，通过 Triton 和 Gluon 等开源 GPU 编程语言重写生产 kernels，实现端到端服务成本降低 20%。Luna 现已成为市场上最便宜的前沿竞争模型，比 Google Gemini 3.1 Flash-Lite ($0.025/$1.50) 和 Anthropic 的 Claude Haiku 4.5 ($1/$5) 都更便宜。其输入价格为 Haiku 的 1/5，使其成为成本敏感应用的新基准。这一价格变化正在改变许多开发者的模型选择，Simon Willison 已将其 agent.datasette.io 项目从 Gemini 3.1 Flash-Lite 切换至 Luna。

### 重點
- GPT-5.6 Luna 价格 $0.20/M input、$1.20/M output，相比 Claude Haiku 4.5 ($1/$5) 便宜超过 80%，成为最便宜的前沿模型
- OpenAI 用 GPT-5.6 Sol 通过 Triton 和 Gluon 重写生产 kernel，实现端到端服务成本降低 20%
- Luna 正取代 Gemini 3.1 Flash-Lite 成为开发者成本基准，改变生态中的模型选择格局

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/30/luna-price-drop/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Advancing the price-performance frontier with GPT‐5.6 
Huge price drop from OpenAI today: GPT-5.6 Terra got a 20% reduction, and GPT-5.6 Luna got a massive 80% drop. 
 OpenAI credit 5.6 Sol with enabling this: in How GPT‐5.6 fuses frontier intelligence with frontier efficiency they describe using 5.6 Sol to optimize load balancing, and more impressively to optimize inference itself: 
 
 We also used GPT‐5.6 Sol to optimize the model’s forward pass: the computation that transforms inputs into next-token predictions. Even when individual operations are fast, excess memory movement, synchronization, and inefficient data layouts can leave GPUs idle. To avoid this, GPT‐5.6 Sol found work that could be precomputed, avoided, or parallelized. With Codex, GPT‐5.6 Sol autonomously rewrote and optimized our production kernels, the core code that executes the mathematical operations that make up the model. This worked in part because we’ve trained GPT‐5.6 to be effective at writing and improving kernels in Triton⁠ and Gluon⁠ , two open-source GPU programming languages maintained by OpenAI. These efforts, combined with broader kernel advancements from GPT‐5.6 Sol, reduced end-to-end serving costs by 20%. 
 
 That Luna price drop completely changes the landscape with respect to lower priced models. At $0.20/million tokens for input and $1.20/million for output Luna is now cheaper than Google's Gemini 3.1 Flash-Lite ($.025/$1.50). 
 Anthropic's cheapest current model is Claude Haiku 4.5, and that's $1/$5 - Luna is now 1/5th of that for input, previously it cost the same. 
 My agent.datasette.io demo site was running on Gemini 3.1 Flash-Lite. I've switched it over to Luna.

 Via Hacker News 

 Tags: ai , openai , generative-ai , llms , anthropic , gemini , llm-pricing

</details>