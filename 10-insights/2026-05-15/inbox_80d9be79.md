---
id: inbox_80d9be79
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_80d9be79]]"
title: "datasette-llm-limits 0.1a0"
url: https://simonwillison.net/2026/May/15/datasette-llm-limits/#atom-everything
source: simon-willison
published_at: 2026-05-15T00:42:09+00:00
fetched_at: 2026-05-18T04:02:17.971357+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-llm-limits 0.1a0 插件發佈。此插件搭配 datasette-llm 與 datasette-llm-accountant 使用，在 Datasette 中為 LLM 使用設置成本限制。支持按用戶或全局配置，可設置滾動時間窗口（如 24 小時）與每日支出上限（如 USD 1.00）。適合在公共或多用戶 Datasette 部署中控制 LLM 調用成本。"
key_points:
  - "支持按用戶級別（actor scope）或全局設置 LLM 支出限制，配置粒度細緻"
  - "滾動時間窗口設計（rolling-24h）防止用戶在固定周期內濫用 LLM API 調用"
  - "與 datasette-llm 與 datasette-llm-accountant 插件配合，形成完整的 LLM 使用追蹤與成本控制體系"
tags: [datasette, llm, cost-management, plugin, datasette-llm]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-llm-limits 0.1a0

datasette-llm-limits 0.1a0 插件發佈。此插件搭配 datasette-llm 與 datasette-llm-accountant 使用，在 Datasette 中為 LLM 使用設置成本限制。支持按用戶或全局配置，可設置滾動時間窗口（如 24 小時）與每日支出上限（如 USD 1.00）。適合在公共或多用戶 Datasette 部署中控制 LLM 調用成本。

### 重點
- 支持按用戶級別（actor scope）或全局設置 LLM 支出限制，配置粒度細緻
- 滾動時間窗口設計（rolling-24h）防止用戶在固定周期內濫用 LLM API 調用
- 與 datasette-llm 與 datasette-llm-accountant 插件配合，形成完整的 LLM 使用追蹤與成本控制體系

**原文：** [simon-willison](https://simonwillison.net/2026/May/15/datasette-llm-limits/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# datasette-llm-limits 0.1a0

Release: datasette-llm-limits 0.1a0 
 This plugin works in conjunction with datasette-llm and datasette-llm-accountant to let you configure a per-user (or global) spending limit for LLM usage inside of Datasette. Configuration looks something like this: 
 plugins :
 datasette-llm-limits :
 limits :
 per-user-daily :
 scope : actor 
 window : rolling-24h 
 amount_usd : 1.00 
 
 
 
 Tags: llm , datasette

</details>