---
id: inbox_e0f2b793
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/0132-hackernews-deepseek-v4almost-on-the-frontier-c788]]"
title: "DeepSeek V4—almost on the frontier"
url: https://simonwillison.net/2026/Apr/24/deepseek-v4/
source: hackernews
published_at: 2026-05-01T16:52:43+00:00
fetched_at: 2026-05-03T02:09:22.162390+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "DeepSeek 發布 V4 預覽模型系列，包括 V4-Pro (1.6T 參數，49B active) 和 V4-Flash (284B 參數，13B active)，均支援 100 萬 token 上下文和 MIT 許可證。V4-Pro 成為現今最大的開源權重模型，超過 Kimi K2.6 和 GLM-5.1；其效率突破：僅需 27% 的單 token FLOPs 相比 V3.2，性能落後 SOTA 約 3-6 個月。定價優勢明顯：V4-Flash 每百萬 token $0.14 input (便宜於 GPT-5.4 Nano 的 $0.20)，V4-Pro $1.74 input (遠低於 Claude Sonnet 4.6 的 $3)，成為最便宜的前沿級模型。Flash 可透過量化在高端硬體本地運行。"
key_points:
  - "V4-Pro 1.6T 參數 (49B active) + V4-Flash 284B (13B active)，均 1M token context，MIT 許可"
  - "效率突破：V4-Pro 僅用 27% FLOPs (vs V3.2)；規模最大開源權重模型"
  - "定價優勢：V4-Flash $0.14/M tokens (vs GPT Nano $0.20)、V4-Pro $1.74/M (vs Claude Sonnet $3)，最便宜前沿級模型"
tags: [deepseek-v4, foundation-model, open-weights, cost-efficiency, llm]
topics: []
importance: 5
novelty: 5
insight_quality: 5
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## DeepSeek V4—almost on the frontier

DeepSeek 發布 V4 預覽模型系列，包括 V4-Pro (1.6T 參數，49B active) 和 V4-Flash (284B 參數，13B active)，均支援 100 萬 token 上下文和 MIT 許可證。V4-Pro 成為現今最大的開源權重模型，超過 Kimi K2.6 和 GLM-5.1；其效率突破：僅需 27% 的單 token FLOPs 相比 V3.2，性能落後 SOTA 約 3-6 個月。定價優勢明顯：V4-Flash 每百萬 token $0.14 input (便宜於 GPT-5.4 Nano 的 $0.20)，V4-Pro $1.74 input (遠低於 Claude Sonnet 4.6 的 $3)，成為最便宜的前沿級模型。Flash 可透過量化在高端硬體本地運行。

### 重點
- V4-Pro 1.6T 參數 (49B active) + V4-Flash 284B (13B active)，均 1M token context，MIT 許可
- 效率突破：V4-Pro 僅用 27% FLOPs (vs V3.2)；規模最大開源權重模型
- 定價優勢：V4-Flash $0.14/M tokens (vs GPT Nano $0.20)、V4-Pro $1.74/M (vs Claude Sonnet $3)，最便宜前沿級模型

**原文：** [hackernews](https://simonwillison.net/2026/Apr/24/deepseek-v4/)