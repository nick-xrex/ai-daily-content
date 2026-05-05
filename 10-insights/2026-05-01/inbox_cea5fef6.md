---
id: inbox_cea5fef6
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/0820-hackernews-using-underdrawings-for-accurate-text-an-6872]]"
title: "Using “underdrawings” for accurate text and numbers"
url: https://samcollins.blog/underdrawings/
source: hackernews
published_at: 2026-05-01T18:07:28+00:00
fetched_at: 2026-05-05T08:52:00.804203+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者介紹「underdrawings」技巧——用 SVG 或 HTML 等確定性工具生成精確定位的文字與數字底圖，再將其輸入多模態圖像生成模型並要求風格化轉換。此方法巧妙規避了生成式 AI 在文字準確性方面的內在弱點，通過分工讓確定性工具負責精度運算、AI 負責視覺創意。作者以生成含正確編號的 50 格遊戲棋盤為例，展示該技巧相比直接文字提示的顯著改進。這是低成本高效益的多模態 AI 提示工程模式。"
key_points:
  - "兩層架構：SVG/HTML 底圖層精確定位文字與數字；AI 生成層在其上進行風格化轉換"
  - "規避 AI 純生成文字的準確性問題，改由確定性工具負責數學運算，AI 專注視覺創新"
  - "實例驗證：50 格遊戲棋盤編號，直接提示失敗、underdrawings 成功"
tags: [prompt-engineering, multimodal-ai, image-generation, accuracy-pattern]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Using “underdrawings” for accurate text and numbers

作者介紹「underdrawings」技巧——用 SVG 或 HTML 等確定性工具生成精確定位的文字與數字底圖，再將其輸入多模態圖像生成模型並要求風格化轉換。此方法巧妙規避了生成式 AI 在文字準確性方面的內在弱點，通過分工讓確定性工具負責精度運算、AI 負責視覺創意。作者以生成含正確編號的 50 格遊戲棋盤為例，展示該技巧相比直接文字提示的顯著改進。這是低成本高效益的多模態 AI 提示工程模式。

### 重點
- 兩層架構：SVG/HTML 底圖層精確定位文字與數字；AI 生成層在其上進行風格化轉換
- 規避 AI 純生成文字的準確性問題，改由確定性工具負責數學運算，AI 專注視覺創新
- 實例驗證：50 格遊戲棋盤編號，直接提示失敗、underdrawings 成功

**原文：** [hackernews](https://samcollins.blog/underdrawings/)