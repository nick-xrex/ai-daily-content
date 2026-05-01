---
id: inbox_64e1df60
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/1257-medium-tag-claude-stop-overfeeding-your-claude-md-ebb7]]"
title: "Stop Overfeeding Your CLAUDE.md"
url: https://medium.com/@shyam_verma/stop-overfeeding-your-claude-md-df973325d101?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-01T10:16:16+00:00
fetched_at: 2026-05-01T13:26:19.825698+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章警示 Claude Pro 使用者在 CLAUDE.md 檔案中累積過多內容導致 context window 快速飽和的陷阱。常見症狀為使用者在下午 2 時前即耗盡 100% token 配額，被迫等待 5 小時配額重置。根本原因是每次會話系統自動載入整個 CLAUDE.md 內容，任何累積在其中的指示、規則、程式碼片段等都會無形消耗寶貴的 context 預算。文章建議精簡 CLAUDE.md，只保留核心、高頻使用的指示。此優化對高頻 Claude Code 使用者具有實務價值。"
key_points:
  - "CLAUDE.md 過度填充是 context window 快速耗盡的根本原因，通常午餐時已達配額上限"
  - "每次會話自動載入全部 CLAUDE.md 導致無效 context 消耗，降低可用預算"
  - "解決方案：精簡 CLAUDE.md 為核心內容，避免無限累積規則和程式碼片段"
tags: [claude-code, context-window, claude-md, rate-limiting, optimization]
topics: [foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Stop Overfeeding Your CLAUDE.md

文章警示 Claude Pro 使用者在 CLAUDE.md 檔案中累積過多內容導致 context window 快速飽和的陷阱。常見症狀為使用者在下午 2 時前即耗盡 100% token 配額，被迫等待 5 小時配額重置。根本原因是每次會話系統自動載入整個 CLAUDE.md 內容，任何累積在其中的指示、規則、程式碼片段等都會無形消耗寶貴的 context 預算。文章建議精簡 CLAUDE.md，只保留核心、高頻使用的指示。此優化對高頻 Claude Code 使用者具有實務價值。

### 重點
- CLAUDE.md 過度填充是 context window 快速耗盡的根本原因，通常午餐時已達配額上限
- 每次會話自動載入全部 CLAUDE.md 導致無效 context 消耗，降低可用預算
- 解決方案：精簡 CLAUDE.md 為核心內容，避免無限累積規則和程式碼片段

**原文：** [medium-tag-claude](https://medium.com/@shyam_verma/stop-overfeeding-your-claude-md-df973325d101?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@shyam_verma/stop-overfeeding-your-claude-md-df973325d101?source=rss------claude-5"><img src="https://cdn-images-1.medium.com/max/964/0*ggxQlwGmpgx5kQxl.png" width="964" /></a></p><p class="medium-feed-snippet">Your Claude Pro subscription hits 100% by 2pm. You stare at the 5-hour reset timer.</p><p class="medium-feed-link"><a href="https://medium.com/@shyam_verma/stop-overfeeding-your-claude-md-df973325d101?source=rss------claude-5">Continue reading on Medium »</a></p></div>

</details>