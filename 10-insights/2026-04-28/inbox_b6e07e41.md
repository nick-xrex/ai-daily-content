---
id: inbox_b6e07e41
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0248-medium-tag-claude-agentic-ai-the-hard-way-part-2-the-user-6481]]"
title: "Agentic AI The Hard Way — Part 2 The User Experience"
url: https://medium.com/@CCH0/agentic-ai-the-hard-way-part-2-the-user-experience-29150481c476?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-04-28T00:41:53+00:00
fetched_at: 2026-04-28T03:05:50.200271+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文（系列第二篇）展示 PropSearch 房產搜索應用的用戶體驗設計。用戶通過自然語言對話（如「找奧斯汀地區 50 萬美元以下的 3 臥室房屋」）與代理互動，系統在對話中漸進式精化搜索條件、保留前次篩選、點擊卡片顯示內聯詳細資訊。技術堆疊包括 React 18 + TypeScript + Tailwind CSS + react-leaflet + OpenStreetMap，使用 Server-Sent Events 流式傳輸。展示 agentic UI 的實際應用模式。"
key_points:
  - "漸進式精化：系統保留前次篩選條件，僅更新使用者修改的欄位，無需重新開始"
  - "上下文持久化：新會話時自動載入前次預算和位置，提升用戶體驗連貫性"
  - "技術堆疊：React 18 + OpenStreetMap + Server-Sent Events 實現流式回應"
tags: [agentic-ai, user-experience, conversation-design, react, property-search]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Agentic AI The Hard Way — Part 2 The User Experience

本文（系列第二篇）展示 PropSearch 房產搜索應用的用戶體驗設計。用戶通過自然語言對話（如「找奧斯汀地區 50 萬美元以下的 3 臥室房屋」）與代理互動，系統在對話中漸進式精化搜索條件、保留前次篩選、點擊卡片顯示內聯詳細資訊。技術堆疊包括 React 18 + TypeScript + Tailwind CSS + react-leaflet + OpenStreetMap，使用 Server-Sent Events 流式傳輸。展示 agentic UI 的實際應用模式。

### 重點
- 漸進式精化：系統保留前次篩選條件，僅更新使用者修改的欄位，無需重新開始
- 上下文持久化：新會話時自動載入前次預算和位置，提升用戶體驗連貫性
- 技術堆疊：React 18 + OpenStreetMap + Server-Sent Events 實現流式回應

**原文：** [medium-tag-claude](https://medium.com/@CCH0/agentic-ai-the-hard-way-part-2-the-user-experience-29150481c476?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@CCH0/agentic-ai-the-hard-way-part-2-the-user-experience-29150481c476?source=rss------claude-5"><img src="https://cdn-images-1.medium.com/max/2600/0*sZ7FmEbzQ1b4d2-E" width="3276" /></a></p><p class="medium-feed-snippet">Before getting into how it&#x2019;s built, here&#x2019;s what using it actually looks like.</p><p class="medium-feed-link"><a href="https://medium.com/@CCH0/agentic-ai-the-hard-way-part-2-the-user-experience-29150481c476?source=rss------claude-5">Continue reading on Medium »</a></p></div>

</details>