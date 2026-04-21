---
id: inbox_3dd12bfd
date: 2026-04-20
source_ref: "[[00-inbox/.../inbox_3dd12bfd]]"
title: "Claude Token Counter, now with model comparisons"
url: https://simonwillison.net/2026/Apr/20/claude-token-counts/#atom-everything
source: (resumed)
published_at: 2026-04-20T00:50:45+00:00
fetched_at: 2026-04-21T02:36:17.450863+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 升級 Claude Token Counter 工具，支援多個模型版本比較。Opus 4.7 啟用新 tokenizer，對同樣內容產生 1.0–1.35 倍 tokens（系統提示測試為 1.46 倍）。高解析度圖像支援提升到 2,576px（~3.75MP），但同解析度成本相近。PDF 測試顯示 1.08 倍差異。儘管定價與 Opus 4.6 相同（$5/M input、$25/M output），token 膨脹預期造成約 40% 成本增加，開發者需重新評估預算。"
key_points:
  - "Opus 4.7 tokenizer 變更：相同文本對應 1.46× tokens（vs 4.6），系統提示最為明顯"
  - "高解析度圖像支援增至 3.75MP（vs 前版本 ~1MP），但標準解析度 token 成本無變化"
  - "相同定價下實際成本增加 ~40%，長期 API 預算需重新評估"
tags: [claude, tokenization, pricing, opus-4.7, cost-analysis]
topics: [foundation_models.claude]
importance: 4
novelty: 4
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude Token Counter, now with model comparisons

Simon Willison 升級 Claude Token Counter 工具，支援多個模型版本比較。Opus 4.7 啟用新 tokenizer，對同樣內容產生 1.0–1.35 倍 tokens（系統提示測試為 1.46 倍）。高解析度圖像支援提升到 2,576px（~3.75MP），但同解析度成本相近。PDF 測試顯示 1.08 倍差異。儘管定價與 Opus 4.6 相同（$5/M input、$25/M output），token 膨脹預期造成約 40% 成本增加，開發者需重新評估預算。

### 重點
- Opus 4.7 tokenizer 變更：相同文本對應 1.46× tokens（vs 4.6），系統提示最為明顯
- 高解析度圖像支援增至 3.75MP（vs 前版本 ~1MP），但標準解析度 token 成本無變化
- 相同定價下實際成本增加 ~40%，長期 API 預算需重新評估

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/20/claude-token-counts/#atom-everything)