---
id: inbox_8fcd5032
date: 2026-04-20
source_ref: "[[00-inbox/.../inbox_8fcd5032]]"
title: "Pretext.js Bypasses DOM Layout Reflow, Enabling Advanced UX Patterns at 120 FPS"
url: https://www.infoq.com/news/2026/04/pretext-js-120fps-text-layout/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-04-20T12:59:00+00:00
fetched_at: 2026-04-22T00:40:28.263134+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Midjourney 工程師 Cheng Lou 發佈 Pretext，一個僅 15KB 的開源 TypeScript 庫，透過直接計算文本測量和版面配置而繞過瀏覽器 DOM 佈局重排機制。此技術使無限列表、砌體佈局和滾動位置錨定等複雜 UX 模式能以 60~120 fps 穩定運行，達成過去受制於瀏覽器性能的目標。Pretext 使用 AI 迴圈反向工程 DOM 佈局演算法而建，展示 AI 輔助工程在工具開發中的實踐價值。"
key_points:
  - "15KB 庫繞過 DOM layout reflow，達成 60-120 fps 複雜 UI 模式渲染"
  - "啟用無限列表、砌體佈局、滾動錨定等過去難以優化的高級 UX 模式"
  - "用 AI 反向工程 DOM 計算邏輯的案例，展示 AI 輔助工具開發的可行性"
tags: [performance-optimization, text-layout, dom-bypass, ui-patterns, typescript]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Pretext.js Bypasses DOM Layout Reflow, Enabling Advanced UX Patterns at 120 FPS

Midjourney 工程師 Cheng Lou 發佈 Pretext，一個僅 15KB 的開源 TypeScript 庫，透過直接計算文本測量和版面配置而繞過瀏覽器 DOM 佈局重排機制。此技術使無限列表、砌體佈局和滾動位置錨定等複雜 UX 模式能以 60~120 fps 穩定運行，達成過去受制於瀏覽器性能的目標。Pretext 使用 AI 迴圈反向工程 DOM 佈局演算法而建，展示 AI 輔助工程在工具開發中的實踐價值。

### 重點
- 15KB 庫繞過 DOM layout reflow，達成 60-120 fps 複雜 UI 模式渲染
- 啟用無限列表、砌體佈局、滾動錨定等過去難以優化的高級 UX 模式
- 用 AI 反向工程 DOM 計算邏輯的案例，展示 AI 輔助工具開發的可行性

**原文：** [infoq-main](https://www.infoq.com/news/2026/04/pretext-js-120fps-text-layout/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Pretext.js Bypasses DOM Layout Reflow, Enabling Advanced UX Patterns at 120 FPS

<img src="https://res.infoq.com/news/2026/04/pretext-js-120fps-text-layout/en/headerimage/generatedHeaderImage-1776650733551.jpg" /><p>Cheng Lou, a Midjourney engineer, recently released Pretext, a 15KB open-source TypeScript library that measures and lays out text without browser layout reflows, enabling advanced UX/UI patterns like infinite lists, masonry layouts, and scroll position anchoring to run at 60-120 fps. Pretext was built using an AI loop that reverse-engineered the DOM’s layout calculations.</p> <i>By Bruno Couriol</i>

</details>