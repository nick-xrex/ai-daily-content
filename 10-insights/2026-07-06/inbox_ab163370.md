---
id: inbox_ab163370
date: 2026-07-06
source_ref: "[[00-inbox/2026-07-06/2254-rtk-releases-dev-0-44-0-rc-309-5bfc]]"
title: "dev-0.44.0-rc.309"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.309
source: rtk-releases
published_at: 2026-07-06T08:03:57+00:00
fetched_at: 2026-07-07T00:38:26.162077+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.44.0-rc.309 修復 grep 命令的上下文分隔符處理，確保非相鄰匹配區塊之間的 -- 分隔符正確保留。此修復防止 grep 搜尋結果中分隔符意外消失或錯誤合併，提升結果可讀性和可解析性。"
key_points:
  - "Grep 分隔符修復：保留非相鄰匹配區塊間的 -- 分隔符，防止結果混淆"
tags: [grep, bug-fix, separator-handling]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.44.0-rc.309

RTK dev-0.44.0-rc.309 修復 grep 命令的上下文分隔符處理，確保非相鄰匹配區塊之間的 -- 分隔符正確保留。此修復防止 grep 搜尋結果中分隔符意外消失或錯誤合併，提升結果可讀性和可解析性。

### 重點
- Grep 分隔符修復：保留非相鄰匹配區塊間的 -- 分隔符，防止結果混淆

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.309)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #2836 from guyoron1/fix/grep-context-separator 

 fix(grep): preserve -- separator between non-adjacent match blocks

</details>