---
id: inbox_585b1b8d
date: 2026-08-06
source_ref: "[[00-inbox/.../inbox_585b1b8d]]"
title: "I Lost 40% of My Best Post’s Clicks and Didn’t Notice for Three Weeks"
url: https://medium.com/@jonathanimms/i-lost-40-of-my-best-posts-clicks-and-didn-t-notice-for-three-weeks-73cf2df2c8de?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-08-06T21:38:25+00:00
fetched_at: 2026-08-07T01:32:22.031680+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者分享用 Claude 搭建 Google Search Console 監視工具的實踐案例。系統架構為：Node 腳本定期拉取 Search Console 數據 → 確定性程式碼進行噪音過濾 → Claude 進行分析和報告撰寫。作者個人在三週內未察覺最優文章流量下降 40%，後來使用此工具方才發現異常。案例展示混合架構（確定性程式碼 + LLM）在監視與異常檢測中的實踐應用。"
key_points:
  - "Claude 輔助搭建 Search Console 監視工具：Node → 過濾 → Claude 分析流程"
  - "實際案例：未及時發現最優文章流量下降 40%（三週時間窗口）"
  - "混合架構設計：確定性程式碼負責數據提取/過濾，Claude 負責智能分析和報告生成"
tags: [claude-application, search-console, monitoring-tool, hybrid-architecture]
topics: [foundation_models.claude]
importance: 2
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## I Lost 40% of My Best Post’s Clicks and Didn’t Notice for Three Weeks

作者分享用 Claude 搭建 Google Search Console 監視工具的實踐案例。系統架構為：Node 腳本定期拉取 Search Console 數據 → 確定性程式碼進行噪音過濾 → Claude 進行分析和報告撰寫。作者個人在三週內未察覺最優文章流量下降 40%，後來使用此工具方才發現異常。案例展示混合架構（確定性程式碼 + LLM）在監視與異常檢測中的實踐應用。

### 重點
- Claude 輔助搭建 Search Console 監視工具：Node → 過濾 → Claude 分析流程
- 實際案例：未及時發現最優文章流量下降 40%（三週時間窗口）
- 混合架構設計：確定性程式碼負責數據提取/過濾，Claude 負責智能分析和報告生成

**原文：** [medium-tag-claude](https://medium.com/@jonathanimms/i-lost-40-of-my-best-posts-clicks-and-didn-t-notice-for-three-weeks-73cf2df2c8de?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---claude-5"
author: "Jonathan Imms"
published_at: 2026-08-06T21:38:25+00:00
fetched_at: 2026-08-06T22:53:48.603941+00:00
content_hash: "e4dbd619780c50fd0f8edb974b83b7583a3b32c49a38e252413c1fb999281e3c"
lang: en
caption_quality: None
raw: true
topics: []
---

# I Lost 40% of My Best Post’s Clicks and Didn’t Notice for Three Weeks

So I built a Claude-powered Search Console monitor: a Node script pulls the data, deterministic code filters the noise, and Claude writes&#x2026; Continue reading on Medium »

</details>