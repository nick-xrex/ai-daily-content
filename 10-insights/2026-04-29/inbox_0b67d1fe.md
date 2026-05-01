---
id: inbox_0b67d1fe
date: 2026-04-29
source_ref: "[[00-inbox/2026-04-29/youtube/1257-youtube-ai-engineer-everything-i-learned-training-frontier-s-d9fa]]"
title: "Everything I Learned Training Frontier Small Models — Maxime Labonne, Liquid AI"
url: https://www.youtube.com/watch?v=fLUtUkqYHnQ
source: youtube-ai-engineer
published_at: 2026-04-29T12:00:06+00:00
fetched_at: 2026-05-01T13:16:26.292385+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Liquid AI 預訓練負責人 Maxime Labonne 深度剖析邊界小模型（350M–24B 參數）的訓練原則。小模型與大模型本質不同：(1) 記憶受限（hardware 邊界），(2) 知識容量低故需 task-specific 優化而非通用 chatbot，(3) 延遲敏感需極速推理。具體案例：Gemma 3 270M embedding 佔 63% 參數（效能參數僅 37%），而 Liquid 的 LFM 2 通過 gated short convolution 在 on-device profiling 驅動下實現 latency 遠優於 sliding window attention。發布了 VLM 450M 和 350M text 模型於 Hugging Face。"
key_points:
  - "小模型三特性 !== 大模型縮小版：memory-bound, low knowledge capacity, latency-sensitive，需原則性重新設計而非單純參數削減"
  - "架構創新案例：gated short convolution 相比 Gemma 的 sliding window attention 和 GQA 成本更低，proof 通過 on-device profiling（真實硬體）而非理論分析"
  - "嵌入層 bloat 問題：Gemma 3 270M 的 63% 參數浪費在嵌入層（distillation 副產品），有效知識參數僅 37%，提示架構優化潛力"
tags: [small-models, edge-deployment, liquid-ai, model-architecture, latency-optimization]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## Everything I Learned Training Frontier Small Models — Maxime Labonne, Liquid AI

Liquid AI 預訓練負責人 Maxime Labonne 深度剖析邊界小模型（350M–24B 參數）的訓練原則。小模型與大模型本質不同：(1) 記憶受限（hardware 邊界），(2) 知識容量低故需 task-specific 優化而非通用 chatbot，(3) 延遲敏感需極速推理。具體案例：Gemma 3 270M embedding 佔 63% 參數（效能參數僅 37%），而 Liquid 的 LFM 2 通過 gated short convolution 在 on-device profiling 驅動下實現 latency 遠優於 sliding window attention。發布了 VLM 450M 和 350M text 模型於 Hugging Face。

### 重點
- 小模型三特性 !== 大模型縮小版：memory-bound, low knowledge capacity, latency-sensitive，需原則性重新設計而非單純參數削減
- 架構創新案例：gated short convolution 相比 Gemma 的 sliding window attention 和 GQA 成本更低，proof 通過 on-device profiling（真實硬體）而非理論分析
- 嵌入層 bloat 問題：Gemma 3 270M 的 63% 參數浪費在嵌入層（distillation 副產品），有效知識參數僅 37%，提示架構優化潛力

**原文：** [youtube-ai-engineer](https://www.youtube.com/watch?v=fLUtUkqYHnQ)