---
id: inbox_15bf43c9
date: 2026-07-06
source_ref: "[[00-inbox/.../inbox_15bf43c9]]"
title: "tencent/Hy3"
url: https://simonwillison.net/2026/Jul/6/hy3/#atom-everything
source: simon-willison
published_at: 2026-07-06T23:57:35+00:00
fetched_at: 2026-07-08T01:03:27.954418+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "騰訊推出 Hy3，一個 295B 參數的稀疏混合專家（MoE）模型，實現 21B 活躍參數和 3.8B MTP 層參數的高效架構。性能與具有 2-5 倍參數的旗艦開源模型相媲美，支援 256K 上下文長度。完整版本 598GB、FP8 量化版本 300GB（節省 50% 存儲空間）。已開源（Apache 2.0）並免費在 OpenRouter 提供至 7 月 21 日，展示中國 AI 廠商在模型效率與開源生態的進展。"
key_points:
  - "Hy3 MoE 架構實現參數效率突破：295B 總參數、21B 活躍參數、3.8B MTP 層，推理成本大幅降低"
  - "性能與 2-5 倍參數的旗艦模型相當，支援 256K 上下文，FP8 量化版 300GB（相比完整版節省 50%）"
  - "由騰訊開源（Apache 2.0），免費試用至 7 月 21 日，展示中國開源 AI 競爭力"
tags: [moe-models, llm-release, tencent-hy3, model-efficiency, open-source]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## tencent/Hy3

騰訊推出 Hy3，一個 295B 參數的稀疏混合專家（MoE）模型，實現 21B 活躍參數和 3.8B MTP 層參數的高效架構。性能與具有 2-5 倍參數的旗艦開源模型相媲美，支援 256K 上下文長度。完整版本 598GB、FP8 量化版本 300GB（節省 50% 存儲空間）。已開源（Apache 2.0）並免費在 OpenRouter 提供至 7 月 21 日，展示中國 AI 廠商在模型效率與開源生態的進展。

### 重點
- Hy3 MoE 架構實現參數效率突破：295B 總參數、21B 活躍參數、3.8B MTP 層，推理成本大幅降低
- 性能與 2-5 倍參數的旗艦模型相當，支援 256K 上下文，FP8 量化版 300GB（相比完整版節省 50%）
- 由騰訊開源（Apache 2.0），免費試用至 7 月 21 日，展示中國開源 AI 競爭力

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/6/hy3/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# tencent/Hy3

tencent/Hy3 
New Apache 2.0 licensed model from Tencent in China: 
 
 Hy3 is a 295B-parameter Mixture-of-Experts (MoE) model with 21B active parameters and 3.8B MTP layer parameters, developed by the Tencent Hy Team. Following the Hy3 Preview launch in late April, we gathered feedback from 50+ products and scaled up post-training with higher quality data. Today, we introduce Hy3, which outperforms similar-size models and rivals flagship open-source models with 2-5x parameters. It also shows significant gains in utility across various products and productivity tasks. 
 
 The full-sized model is 598GB on Hugging Face, and the FP8 quantized one is 300GB . The context length is 256K. 
 It's available for free on OpenRouter until July 21st . I had it "Generate an SVG of a pelican riding a bicycle" there and got this: 
 

 Tags: ai , generative-ai , llms , pelican-riding-a-bicycle , llm-release , ai-in-china

</details>