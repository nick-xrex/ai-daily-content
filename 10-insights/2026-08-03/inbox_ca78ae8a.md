---
id: inbox_ca78ae8a
date: 2026-08-03
source_ref: "[[00-inbox/.../inbox_ca78ae8a]]"
title: "Article: Enabling Evolutionary Architecture Through the Preservation of Change Locality"
url: https://www.infoq.com/articles/evolutionary-architecture-change-locality/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-08-03T11:00:00+00:00
fetched_at: 2026-08-04T01:58:03.054283+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文探討軟體進化架構中的邊界漂移問題。軟體邊界在跨團隊協作中容易漸進漂移，導致簡單功能突然需要複雜的跨團隊協商，增加整體認知負載。作者提出社技策略恢復域邊界：(1)重新分配與邊界相關的責任(redistributing mechanics)，(2)暴露核心政策而非隱藏(exposing essential policy)，(3)排演異常路徑驗證邊界強度(rehearsing exception paths)。這些策略通過減少隱性邊界違反和跨域協調成本，使團隊能獨立演進系統。文章作者為 Michael Fischer、Nicholas Lawrence 和 Monica Karekar。"
key_points:
  - "邊界漂移是隱性信號：簡單需求突然需跨團隊協商，說明邊界定義已鬆動"
  - "社技策略三角：責任重分配、政策暴露、邊界測試—非純架構設計"
  - "Change locality 保持是大規模系統可擴展的基礎，減少團隊外部協調"
tags: [evolutionary-architecture, change-locality, sociotechnical-design, boundary-management]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: Enabling Evolutionary Architecture Through the Preservation of Change Locality

本文探討軟體進化架構中的邊界漂移問題。軟體邊界在跨團隊協作中容易漸進漂移，導致簡單功能突然需要複雜的跨團隊協商，增加整體認知負載。作者提出社技策略恢復域邊界：(1)重新分配與邊界相關的責任(redistributing mechanics)，(2)暴露核心政策而非隱藏(exposing essential policy)，(3)排演異常路徑驗證邊界強度(rehearsing exception paths)。這些策略通過減少隱性邊界違反和跨域協調成本，使團隊能獨立演進系統。文章作者為 Michael Fischer、Nicholas Lawrence 和 Monica Karekar。

### 重點
- 邊界漂移是隱性信號：簡單需求突然需跨團隊協商，說明邊界定義已鬆動
- 社技策略三角：責任重分配、政策暴露、邊界測試—非純架構設計
- Change locality 保持是大規模系統可擴展的基礎，減少團隊外部協調

**原文：** [infoq-main](https://www.infoq.com/articles/evolutionary-architecture-change-locality/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Article: Enabling Evolutionary Architecture Through the Preservation of Change Locality

Why do simple features suddenly require cross-team negotiations? In this article, explore how boundary drift quietly destroys change locality and increases cognitive load across teams. Learn practical sociotechnical strategies - redistributing mechanics, exposing essential policy, and rehearsing exception paths - to restore domain boundaries and enable a truly evolutionary software architecture. By Michael Fischer, Nicholas Lawrence, Monica Karekar

</details>