---
id: inbox_b50ef176
date: 2026-05-13
source_ref: "[[00-inbox/.../inbox_b50ef176]]"
title: "Article: The Mathematics of Backlogs: Capacity Planning for Queue Recovery"
url: https://www.infoq.com/articles/capacity-planning-queue-recovery/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-13T09:00:00+00:00
fetched_at: 2026-05-18T03:34:15.026918+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "分布式系統中的待辦項積壓並非黑盒，而是可用數學公式精確計算的可控問題。文章提供實用的容量規劃公式，包括待辦項排空時間計算、消費者裕度設定和自動擴展觸發器配置。同時詳細剖析了常見失敗模式：重試放大（retry amplification）、元穩態（metastable state）和級聯管道瓶頸。文章強調何時應採用負載脫落（load shedding）而非持續排空，為大規模隊列系統的設計提供了數學理論基礎。"
key_points:
  - "容量規劃的數學框架：計算待辦排空時間、消費者裕度、自動擴展觸發器的公式"
  - "失敗模式分類：重試放大（retry amplification）、元穩態（metastable state）、級聯瓶頸（cascading bottleneck）"
  - "策略選擇：明確何時應採用負載脫落（load shedding）而非持續排空積壓"
tags: [queue-management, capacity-planning, distributed-systems]
topics: []
importance: 2
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: The Mathematics of Backlogs: Capacity Planning for Queue Recovery

分布式系統中的待辦項積壓並非黑盒，而是可用數學公式精確計算的可控問題。文章提供實用的容量規劃公式，包括待辦項排空時間計算、消費者裕度設定和自動擴展觸發器配置。同時詳細剖析了常見失敗模式：重試放大（retry amplification）、元穩態（metastable state）和級聯管道瓶頸。文章強調何時應採用負載脫落（load shedding）而非持續排空，為大規模隊列系統的設計提供了數學理論基礎。

### 重點
- 容量規劃的數學框架：計算待辦排空時間、消費者裕度、自動擴展觸發器的公式
- 失敗模式分類：重試放大（retry amplification）、元穩態（metastable state）、級聯瓶頸（cascading bottleneck）
- 策略選擇：明確何時應採用負載脫落（load shedding）而非持續排空積壓

**原文：** [infoq-main](https://www.infoq.com/articles/capacity-planning-queue-recovery/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Article: The Mathematics of Backlogs: Capacity Planning for Queue Recovery

Backlogs in distributed systems are arithmetic problems, not mysteries. This article provides practical formulas for calculating backlog drain time, sizing consumer headroom, and setting auto-scaling triggers. It covers key failure modes — retry amplification, metastable states, and cascading pipeline bottlenecks — plus when to shed load instead of draining. By Rajesh Kumar Pandey

</details>