---
id: inbox_603d6ed3
date: 2026-07-31
source_ref: "[[00-inbox/2026-07-31/0614-simon-willison-deepseek-ai-deepseek-v4-flash-0731-1d1c]]"
title: "deepseek-ai/DeepSeek-V4-Flash-0731"
url: https://simonwillison.net/2026/Jul/31/deepseek-v4-flash-0731/#atom-everything
source: simon-willison
published_at: 2026-07-31T23:59:44+00:00
fetched_at: 2026-08-01T06:19:57.017790+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "DeepSeek 發布 V4-Flash-0731 模型，304 億參數（Hugging Face 167GB），著重增強代理能力。定價設定為 $0.14 / 百萬 tokens 輸入、$0.27 / 百萬 tokens 輸出，成為當前智能對成本比最優的模型之一。Artificial Analysis 測試將其排名超過參數量更大的 MiniMax M3（428B 模型），在 Intelligence Index vs. Cost Per Intelligence Index Task 圖表上表現優異。Simon Willison 實測顯示，使用預設推理水平時結果較平凡，但將推理水平提升至「high」（via reasoning_effort 參數）後，模型性能顯著改善，達到高質量輸出水準。"
key_points:
  - "DeepSeek V4-Flash-0731：304B 參數，$0.14/$0.27 per million tokens，成本效益超越 428B 的 MiniMax M3"
  - "Artificial Analysis 排名顯示在 Intelligence Index vs. Cost 二維空間上表現超群，價位最具競爭力"
  - "推理水平（reasoning_effort=high）對模型輸出品質影響顯著，預設設置下遠低於高推理水平"
tags: [deepseek, large-language-model, pricing, agentic, inference-optimization]
topics: []
importance: 5
novelty: 5
insight_quality: 3
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## deepseek-ai/DeepSeek-V4-Flash-0731

DeepSeek 發布 V4-Flash-0731 模型，304 億參數（Hugging Face 167GB），著重增強代理能力。定價設定為 $0.14 / 百萬 tokens 輸入、$0.27 / 百萬 tokens 輸出，成為當前智能對成本比最優的模型之一。Artificial Analysis 測試將其排名超過參數量更大的 MiniMax M3（428B 模型），在 Intelligence Index vs. Cost Per Intelligence Index Task 圖表上表現優異。Simon Willison 實測顯示，使用預設推理水平時結果較平凡，但將推理水平提升至「high」（via reasoning_effort 參數）後，模型性能顯著改善，達到高質量輸出水準。

### 重點
- DeepSeek V4-Flash-0731：304B 參數，$0.14/$0.27 per million tokens，成本效益超越 428B 的 MiniMax M3
- Artificial Analysis 排名顯示在 Intelligence Index vs. Cost 二維空間上表現超群，價位最具競爭力
- 推理水平（reasoning_effort=high）對模型輸出品質影響顯著，預設設置下遠低於高推理水平

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/31/deepseek-v4-flash-0731/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

deepseek-ai/DeepSeek-V4-Flash-0731 
The latest release in DeepSeek's V4 family, "with substantially enhanced agentic capabilities". It's 304 billion parameters - 167GB on Hugging Face - but it appears to punch well above its weight. 
 Artificial Analysis rank it ahead of MiniMax M3 - a 428B model. It's $0.14/million input and $0.27/million output pricing means this may currently be the best value-per-intelligence model out there. It's looking very good on the Intelligence Index vs. Cost per Intelligence Index Task chart: 
 
 I got a disappointing pelican from it using the default reasoning level via OpenRouter: 
 
 But when I bumped reasoning level up to high I got something much better : 
 llm -m openrouter/deepseek/deepseek-v4-flash-0731 -t pelican -o reasoning_effort high 
 

 Via Hacker News 

 Tags: ai , generative-ai , llms , pelican-riding-a-bicycle , deepseek , llm-release , openrouter , ai-in-china , artificial-analysis

</details>