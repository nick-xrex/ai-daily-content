---
id: inbox_c926deda
date: 2026-07-28
source_ref: "[[00-inbox/2026-07-28/0109-hackernews-show-hn-i-was-tired-of-opening-2-tabs-fo-4b5f]]"
title: "Show HN: I was tired of opening 2 tabs for every HN link, so I made a userscript"
url: https://github.com/twalichiewicz/HNewhere
source: hackernews
published_at: 2026-07-28T22:09:06+00:00
fetched_at: 2026-07-31T01:14:44.363531+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者為解決 HN 用戶需頻繁切換文章和評論 tab 的問題，開發了一款 userscript。功能：(1) 點擊 HN 連結時，以側邊板在同窗口呈現評論討論，無需額外登入，支援調整大小與自訂；(2) 若文章已在 HN 分享過，script 自動搜尋現有討論執行緒並在頁面右上角加按鈕快速開啟。本工具提升 HN 閱讀體驗，惟與 AI/LLM 無直接相關性。"
key_points:
  - "Userscript 在單窗口側邊板並行顯示 HN 文章與評論，減少 tab 切換"
  - "支持自動檢測已分享文章並提供快速連結按鈕開啟現有評論執行緒"
tags: [userscript, hn-tools, productivity]
topics: []
importance: 1
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: I was tired of opening 2 tabs for every HN link, so I made a userscript

開發者為解決 HN 用戶需頻繁切換文章和評論 tab 的問題，開發了一款 userscript。功能：(1) 點擊 HN 連結時，以側邊板在同窗口呈現評論討論，無需額外登入，支援調整大小與自訂；(2) 若文章已在 HN 分享過，script 自動搜尋現有討論執行緒並在頁面右上角加按鈕快速開啟。本工具提升 HN 閱讀體驗，惟與 AI/LLM 無直接相關性。

### 重點
- Userscript 在單窗口側邊板並行顯示 HN 文章與評論，減少 tab 切換
- 支持自動檢測已分享文章並提供快速連結按鈕開啟現有評論執行緒

**原文：** [hackernews](https://github.com/twalichiewicz/HNewhere)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

HN is great for the links people share, but a big part of the value I get comes from reading the discussion around them. I realized I was always opening the article in one tab and the comments in another, constantly switching back and forth. I figured there was probably a simpler way, so I threw together this userscript to merge the two. 1. Clicking a link from Hacker News opens the article with a side panel containing the discussion. It doesn&#x27;t require your credentials, is resizable, and is easy to tweak if you want to customize it. 2. If you land on an article that has previously been shared on HN, the script finds the existing discussion and adds a button in the top-right to open the panel. Feedback welcome.

</details>