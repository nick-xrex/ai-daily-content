---
id: inbox_ded53ca8
date: 2026-06-20
source_ref: "[[00-inbox/.../inbox_ded53ca8]]"
title: "v2.1.185"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.185
source: claude-code-releases
published_at: 2026-06-20T20:59:19+00:00
fetched_at: 2026-06-21T02:26:56.977700+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.185 發布改善用戶界面提示訊息。當 API 響應超過 20 秒無回應時（之前為 10 秒），IDE 會顯示「等待 API 回應 · 將在 ... 秒後重試」的提示。此新提示比之前的「無 API 回應 · 正在重試 ...」更清楚地傳達等待狀態。超時觸發時間從 10 秒延長至 20 秒，減少誤觸發警告。這是純粹的 UX 優化，沒有功能改變。"
key_points:
  - "等待提示文案改善：「等待 API 回應」更清楚傳達狀態"
  - "超時觸發時間調整：從 10 秒延長至 20 秒"
tags: [claude-code, ux-improvement, v2.1.185]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.185

Claude Code v2.1.185 發布改善用戶界面提示訊息。當 API 響應超過 20 秒無回應時（之前為 10 秒），IDE 會顯示「等待 API 回應 · 將在 ... 秒後重試」的提示。此新提示比之前的「無 API 回應 · 正在重試 ...」更清楚地傳達等待狀態。超時觸發時間從 10 秒延長至 20 秒，減少誤觸發警告。這是純粹的 UX 優化，沒有功能改變。

### 重點
- 等待提示文案改善：「等待 API 回應」更清楚傳達狀態
- 超時觸發時間調整：從 10 秒延長至 20 秒

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.185)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.185

What's changed 
 
 The stream-stall hint now reads "Waiting for API response · will retry in ..." instead of "No response from API · Retrying in ...", and triggers after 20s of silence instead of 10s

</details>