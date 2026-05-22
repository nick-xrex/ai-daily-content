---
id: inbox_45cff1d1
date: 2026-05-20
source_ref: "[[00-inbox/2026-05-20/0036-simon-willison-datasette-agent-charts-0-1a1-f8e6]]"
title: "datasette-agent-charts 0.1a1"
url: https://simonwillison.net/2026/May/20/datasette-agent-charts/#atom-everything
source: simon-willison
published_at: 2026-05-20T14:52:16+00:00
fetched_at: 2026-05-22T00:40:19.137273+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-agent-charts 0.1a1 發布，增強圖表視覺化和互動性。bar 和 waffle charts 無色彩欄位時按數值大小自動使用 sequential color scheme；文本色彩欄位採用 observable10 分類配色；新增交互式 tooltips；修復 waffleY 圖表的代理描述缺失；執行 SQL 前檢查 execute-sql 權限。"
key_points:
  - "彩色映射策略自適應：根據數據類型（連續 vs 分類）自動選擇配色方案，無需手動指定，提升開箱即用體驗"
  - "交互式 tooltips 和執行前權限檢查改進資料探索安全性和易用性"
tags: [datasette-agent, charts, visualization, color-design, ux]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-agent-charts 0.1a1

datasette-agent-charts 0.1a1 發布，增強圖表視覺化和互動性。bar 和 waffle charts 無色彩欄位時按數值大小自動使用 sequential color scheme；文本色彩欄位採用 observable10 分類配色；新增交互式 tooltips；修復 waffleY 圖表的代理描述缺失；執行 SQL 前檢查 execute-sql 權限。

### 重點
- 彩色映射策略自適應：根據數據類型（連續 vs 分類）自動選擇配色方案，無需手動指定，提升開箱即用體驗
- 交互式 tooltips 和執行前權限檢查改進資料探索安全性和易用性

**原文：** [simon-willison](https://simonwillison.net/2026/May/20/datasette-agent-charts/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-agent-charts 0.1a1 
 
 
 More color! Bar and waffle charts without a color column are shaded by magnitude with a sequential color scheme; color columns holding text values use the observable10 categorical scheme. #2 
 Now checks execute-sql permission before running the query to find the column names. 
 Charts now display interactive tooltips. 
 Fixed a bug where waffleY charts were not described to the agent. 
 
 
 
 
 Tags: datasette , datasette-agent

</details>