---
id: inbox_abae07d8
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-rtk-releases-dev-0-44-0-rc-306-6184]]"
title: "dev-0.44.0-rc.306"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.306
source: rtk-releases
published_at: 2026-07-03T10:32:00+00:00
fetched_at: 2026-07-04T01:22:28.333042+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.44.0-rc.306 修復分析模塊的 UTF-8 字符邊界問題，確保顯示字符串截斷時不致觸發 panic，提升多語言環境下的穩定性與可靠性。"
key_points:
  - "修復 UTF-8 邊界截斷導致的 panic，改善多語言支持"
tags: [utf8, internationalization, bugfix]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.44.0-rc.306

RTK dev-0.44.0-rc.306 修復分析模塊的 UTF-8 字符邊界問題，確保顯示字符串截斷時不致觸發 panic，提升多語言環境下的穩定性與可靠性。

### 重點
- 修復 UTF-8 邊界截斷導致的 panic，改善多語言支持

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.306)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #2789 from rtk-ai/fix/analytics-utf8-char-boundary... 

 ...-panic 

 fix(analytics): truncate display strings on UTF-8 char boundaries

</details>