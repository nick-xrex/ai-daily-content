---
id: inbox_34a7992e
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0658-hackernews-an-update-on-github-availability-8f84]]"
title: "An update on GitHub availability"
url: https://github.blog/news-insights/company-news/an-update-on-github-availability/
source: hackernews
published_at: 2026-04-28T10:05:03+00:00
fetched_at: 2026-04-29T07:36:26.606293+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitHub 因應 agentic development workflows 的激增而擴大容量。自 2025 年 12 月後半，軟體開發工作流大幅轉向智能代理驅動，導致 PR 合併量達 90M、commit 達 1.4B、新倉庫 20M/月的指數成長。GitHub 將原先 10X 擴容目標調升至 30X，重點改進包括：(1) webhook 從 MySQL 遷出、重設 session cache、優化認證流程；(2) 隔離 Git 和 GitHub Actions 等關鍵服務；(3) 部分代碼從 Ruby 遷至 Go；(4) 多雲部署提升彈性。四月發生 merge queue 和 session cache 兩起故障，影響 658 倉庫和 2,092 個 PR，推動可用性優先的設計策略。"
key_points:
  - "agentic development 驅動的成長指標：PR 90M、commits 1.4B、新 repos 20M/月（相對於基準的指數級增長）"
  - "容量規劃目標從 10X 升至 30X；大型 monorepo 成為 Git 和 PR 系統的主要瓶頸"
  - "架構改進：webhook MySQL 遷出、merge queue 優化、關鍵服務隔離、Ruby→Go 遷移、多雲部署"
tags: [github, agentic-development, ai-agents, infrastructure-scaling, distributed-systems]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## An update on GitHub availability

GitHub 因應 agentic development workflows 的激增而擴大容量。自 2025 年 12 月後半，軟體開發工作流大幅轉向智能代理驅動，導致 PR 合併量達 90M、commit 達 1.4B、新倉庫 20M/月的指數成長。GitHub 將原先 10X 擴容目標調升至 30X，重點改進包括：(1) webhook 從 MySQL 遷出、重設 session cache、優化認證流程；(2) 隔離 Git 和 GitHub Actions 等關鍵服務；(3) 部分代碼從 Ruby 遷至 Go；(4) 多雲部署提升彈性。四月發生 merge queue 和 session cache 兩起故障，影響 658 倉庫和 2,092 個 PR，推動可用性優先的設計策略。

### 重點
- agentic development 驅動的成長指標：PR 90M、commits 1.4B、新 repos 20M/月（相對於基準的指數級增長）
- 容量規劃目標從 10X 升至 30X；大型 monorepo 成為 Git 和 PR 系統的主要瓶頸
- 架構改進：webhook MySQL 遷出、merge queue 優化、關鍵服務隔離、Ruby→Go 遷移、多雲部署

**原文：** [hackernews](https://github.blog/news-insights/company-news/an-update-on-github-availability/)