---
id: inbox_5bfdf35e
date: 2026-05-17
source_ref: "[[00-inbox/.../inbox_5bfdf35e]]"
title: "I Rebuilt My 2018 Side Project With AI. Here’s What I Actually Learned."
url: https://medium.com/@prashanth17.naik/i-rebuilt-my-2018-side-project-with-ai-heres-what-i-actually-learned-53b276eb9de7?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-17T17:38:35+00:00
fetched_at: 2026-05-18T04:07:02.671123+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "2018年Angular+Firebase側專案因6年技術債累積（版本落後、2MB Bundle、CSS凌亂）瀕臨難維護。作者以Claude為協作者遷移至React 18+Vite+HeroUI v3，發現AI在組件架構轉譯、Angular→React適配、CSS級聯除錯表現優異，但版本特定API知識存誤導風險。遷移後Bundle、CSS行數顯著下降；關鍵領悟：六年舊邏輯仍多數正確，瓶頸在「表達方式」而非核心邏輯；AI縮短反饋迴圈，但須驗證生成代碼對應實際安裝版本。"
key_points:
  - "Angular服務→React Hooks/Zustand轉換時間從週末縮至半日；AI理解原始意圖而非逐行翻譯"
  - "HeroUI v3 CSS @layer級聯除錯：發現根因不在CSS而在JS內聯樣式覆蓋——跨層除錯展示AI多域知識整合價值"
  - "AI版本誤導風險：HeroUI v2 vs v3 Button屬性API差異——必須驗證安裝包而非依賴通用知識"
tags: [ai-pair-programming, legacy-migration, bundle-optimization, react-18, vite]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## I Rebuilt My 2018 Side Project With AI. Here’s What I Actually Learned.

2018年Angular+Firebase側專案因6年技術債累積（版本落後、2MB Bundle、CSS凌亂）瀕臨難維護。作者以Claude為協作者遷移至React 18+Vite+HeroUI v3，發現AI在組件架構轉譯、Angular→React適配、CSS級聯除錯表現優異，但版本特定API知識存誤導風險。遷移後Bundle、CSS行數顯著下降；關鍵領悟：六年舊邏輯仍多數正確，瓶頸在「表達方式」而非核心邏輯；AI縮短反饋迴圈，但須驗證生成代碼對應實際安裝版本。

### 重點
- Angular服務→React Hooks/Zustand轉換時間從週末縮至半日；AI理解原始意圖而非逐行翻譯
- HeroUI v3 CSS @layer級聯除錯：發現根因不在CSS而在JS內聯樣式覆蓋——跨層除錯展示AI多域知識整合價值
- AI版本誤導風險：HeroUI v2 vs v3 Button屬性API差異——必須驗證安裝包而非依賴通用知識

**原文：** [medium-tag-claude](https://medium.com/@prashanth17.naik/i-rebuilt-my-2018-side-project-with-ai-heres-what-i-actually-learned-53b276eb9de7?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---claude-5"
author: "Prashanth Naik"
published_at: 2026-05-17T17:38:35+00:00
fetched_at: 2026-05-17T18:00:43.191571+00:00
content_hash: "68d1dd21e0574f7c2b08d9f2bd4bcc5042532afccf09d34ed9f1416a966f3f74"
lang: en
caption_quality: None
raw: true
topics: []
---

# I Rebuilt My 2018 Side Project With AI. Here’s What I Actually Learned.

A story about technical debt, modern frameworks, and what it feels like to hand the keyboard to an AI pair programmer. Continue reading on Medium »

</details>