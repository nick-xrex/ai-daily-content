---
id: inbox_15fc72bd
date: 2026-01-22
source_ref: "[[00-inbox/2026-01-22/0158-openai-blog-scaling-postgresql-to-power-800-million-fd96]]"
title: "Scaling PostgreSQL to power 800 million ChatGPT users"
url: https://openai.com/index/scaling-postgresql
source: openai-blog
published_at: 2026-01-22T12:00:00+00:00
fetched_at: 2026-04-21T02:23:33.883073+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 揭示了其如何擴展 PostgreSQL 以支持 ChatGPT 的 8 億用戶的技術。該擴展方案使用了副本、快取、速率限制和工作負載隔離等多種技術。OpenAI 成功將 PostgreSQL 擴展至每秒處理數百萬次查詢的規模。這個基礎設施升級是支撐 ChatGPT 全球用戶增長的關鍵。文章提供了實戰級的資料庫優化經驗，包括具體的擴展策略。該技術方案對企業級應用的資料庫設計具有重要參考意義。"
key_points:
  - "PostgreSQL 擴展支持 8 億 ChatGPT 用戶，達到每秒百萬級查詢"
  - "使用副本、快取、速率限制、工作負載隔離等多層技術"
  - "提供企業級資料庫擴展的實戰經驗和最佳實踐"
tags: [database-scaling, postgresql, infrastructure, chatgpt-backend, performance-optimization]
topics: [foundation_models.gpt]
importance: 4
novelty: 3
deep_dive_candidate: false
deep_dive_approved: false
---

## Scaling PostgreSQL to power 800 million ChatGPT users

OpenAI 揭示了其如何擴展 PostgreSQL 以支持 ChatGPT 的 8 億用戶的技術。該擴展方案使用了副本、快取、速率限制和工作負載隔離等多種技術。OpenAI 成功將 PostgreSQL 擴展至每秒處理數百萬次查詢的規模。這個基礎設施升級是支撐 ChatGPT 全球用戶增長的關鍵。文章提供了實戰級的資料庫優化經驗，包括具體的擴展策略。該技術方案對企業級應用的資料庫設計具有重要參考意義。

### 重點
- PostgreSQL 擴展支持 8 億 ChatGPT 用戶，達到每秒百萬級查詢
- 使用副本、快取、速率限制、工作負載隔離等多層技術
- 提供企業級資料庫擴展的實戰經驗和最佳實踐

**原文：** [openai-blog](https://openai.com/index/scaling-postgresql)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

An inside look at how OpenAI scaled PostgreSQL to millions of queries per second using replicas, caching, rate limiting, and workload isolation.

</details>
