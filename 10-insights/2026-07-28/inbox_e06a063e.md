---
id: inbox_e06a063e
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_e06a063e]]"
title: "Remix 3 Beta Preview Ditches React for a Web-Standards Full-Stack Framework"
url: https://www.infoq.com/news/2026/07/remix-3-beta-preview/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-28T09:02:00+00:00
fetched_at: 2026-07-29T03:41:28.056113+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Remix 3 Beta 進行了重大架構轉變，放棄了 React 框架改採 Web 標準 primitives，強調伺服器優先的開發理念。此版本整合 routes、request handlers 和 UI 元件為統一結構，使伺服器擁有完整的請求生命週期控制權。前端層採用了 fork 版的 Preact 作為最小化實現，減少了客戶端的負擔。此轉變反映了當今 Web 開發對性能和標準化的重新評估，打破了過去十年的 React 中心主義。從 Remix 2 遷移至 Remix 3 需要進行實質性的程式碼重構，無平滑的升級路徑。"
key_points:
  - "Remix 3 放棄 React 採用 Web 標準 primitives，架構思維從客戶端轉向伺服器優先"
  - "使用 fork Preact 作為最小化前端層，統一 routes/handlers/UI 結構設計"
  - "從 Remix 2 遷移需實質重構，無平滑升級路徑，採用者需評估遷移成本"
tags: [remix, web-standards, full-stack-framework, preact, server-ownership]
topics: []
importance: 4
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Remix 3 Beta Preview Ditches React for a Web-Standards Full-Stack Framework

Remix 3 Beta 進行了重大架構轉變，放棄了 React 框架改採 Web 標準 primitives，強調伺服器優先的開發理念。此版本整合 routes、request handlers 和 UI 元件為統一結構，使伺服器擁有完整的請求生命週期控制權。前端層採用了 fork 版的 Preact 作為最小化實現，減少了客戶端的負擔。此轉變反映了當今 Web 開發對性能和標準化的重新評估，打破了過去十年的 React 中心主義。從 Remix 2 遷移至 Remix 3 需要進行實質性的程式碼重構，無平滑的升級路徑。

### 重點
- Remix 3 放棄 React 採用 Web 標準 primitives，架構思維從客戶端轉向伺服器優先
- 使用 fork Preact 作為最小化前端層，統一 routes/handlers/UI 結構設計
- 從 Remix 2 遷移需實質重構，無平滑升級路徑，採用者需評估遷移成本

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/remix-3-beta-preview/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Remix 3 Beta Preview Ditches React for a Web-Standards Full-Stack Framework

Remix 3 is a full-stack web framework that moves away from React, focusing on web platform primitives. It integrates routes, request handlers, and UI components into a single structure, utilizing a forked Preact for the frontend. Unlike previous versions, it emphasizes server ownership of the request lifecycle. Migration from Remix 2 is not straightforward, as it requires changes to existing apps. By Daniel Curtis

</details>