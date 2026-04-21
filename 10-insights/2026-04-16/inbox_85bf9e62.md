---
id: inbox_85bf9e62
date: 2026-04-16
source_ref: "[[00-inbox/.../inbox_85bf9e62]]"
title: "Qwen3.6-35B-A3B on my laptop drew me a better pelican than Claude Opus 4.7"
url: https://simonwillison.net/2026/Apr/16/qwen-beats-opus/#atom-everything
source: (resumed)
published_at: 2026-04-16T17:16:52+00:00
fetched_at: 2026-04-21T02:37:41.614180+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Qwen3.6-35B-A3B（20.9GB 量化版本，本地 MacBook 運行）在 SVG 生成任務中超越新發布的 Claude Opus 4.7。Simon Willison 的「pelican riding a bicycle」基準測試顯示，Qwen 正確生成了自行車框架並產出更符合要求的圖像細節，而 Opus 4.7 的自行車框架結構錯誤。即使 Opus 4.7 使用 thinking_level: max 也未能改善表現。補充測試「flamingo riding a unicycle」中，Qwen 同樣贏得勝利。這個結果反映了開源量化模型在特定視覺生成任務上對閉源旗艦模型的優勢。"
key_points:
  - "Qwen3.6-35B-A3B 量化版在本地 MacBook Pro M5 運行時的 SVG 生成精度超越 Claude Opus 4.7，自行車框架和鵜鶘細節更準確"
  - "Claude Opus 4.7 即使啟用 thinking_level: max 模式也無法修正自行車框架結構錯誤"
  - "補充測試「flamingo riding a unicycle」驗證 Qwen 的一致優勢，展示不同模型在視覺任務能力的差異"
tags: [qwen-3.6, claude-opus-4.7, local-llm, svg-generation, model-comparison]
topics: [foundation_models.claude]
importance: 3
novelty: 3
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen3.6-35B-A3B on my laptop drew me a better pelican than Claude Opus 4.7

Qwen3.6-35B-A3B（20.9GB 量化版本，本地 MacBook 運行）在 SVG 生成任務中超越新發布的 Claude Opus 4.7。Simon Willison 的「pelican riding a bicycle」基準測試顯示，Qwen 正確生成了自行車框架並產出更符合要求的圖像細節，而 Opus 4.7 的自行車框架結構錯誤。即使 Opus 4.7 使用 thinking_level: max 也未能改善表現。補充測試「flamingo riding a unicycle」中，Qwen 同樣贏得勝利。這個結果反映了開源量化模型在特定視覺生成任務上對閉源旗艦模型的優勢。

### 重點
- Qwen3.6-35B-A3B 量化版在本地 MacBook Pro M5 運行時的 SVG 生成精度超越 Claude Opus 4.7，自行車框架和鵜鶘細節更準確
- Claude Opus 4.7 即使啟用 thinking_level: max 模式也無法修正自行車框架結構錯誤
- 補充測試「flamingo riding a unicycle」驗證 Qwen 的一致優勢，展示不同模型在視覺任務能力的差異

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/16/qwen-beats-opus/#atom-everything)