---
id: inbox_a3e21db6
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_a3e21db6]]"
title: "Article: The Hard-Stop Rule: From 3 HCM Monoliths to 120 Domain Microservices"
url: https://www.infoq.com/articles/pull-based-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-28T09:00:00+00:00
fetched_at: 2026-07-29T03:41:28.057791+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "一支 HR/薪資軟體團隊在無專門遷移預算的條件下，用 5 年時間將 3 個單體應用成功重構為 120+ 個域微服務。核心策略是「硬停止規則」：所有新功能必須實現為新服務，絕不允許修改舊系統，強制團隊進行漸進式架構演進。團隊採用拉式遷移方式，通過優先級排序和工具自動化來控制成本，避免了大規模重寫的高風險。文章詳細記載了成功的遷移工具鏈、成本控制方法和實踐中遇到的常見問題。此案例為大規模系統演進提供了可復用的模式和實戰教訓，具有廣泛的參考價值。"
key_points:
  - "硬停止規則：新功能永遠實現為新服務，絕不修改舊單體，強制漸進式演進"
  - "拉式遷移搭配無預算約束：通過優先級排序和工具自動化實現成本控制"
  - "5 年時間將 3 個單體演進為 120+ 微服務，涵蓋完整的遷移工具鏈和問題模式"
tags: [microservices-migration, monolith-to-microservices, pull-based-migration, cost-optimization, architecture-evolution]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: The Hard-Stop Rule: From 3 HCM Monoliths to 120 Domain Microservices

一支 HR/薪資軟體團隊在無專門遷移預算的條件下，用 5 年時間將 3 個單體應用成功重構為 120+ 個域微服務。核心策略是「硬停止規則」：所有新功能必須實現為新服務，絕不允許修改舊系統，強制團隊進行漸進式架構演進。團隊採用拉式遷移方式，通過優先級排序和工具自動化來控制成本，避免了大規模重寫的高風險。文章詳細記載了成功的遷移工具鏈、成本控制方法和實踐中遇到的常見問題。此案例為大規模系統演進提供了可復用的模式和實戰教訓，具有廣泛的參考價值。

### 重點
- 硬停止規則：新功能永遠實現為新服務，絕不修改舊單體，強制漸進式演進
- 拉式遷移搭配無預算約束：通過優先級排序和工具自動化實現成本控制
- 5 年時間將 3 個單體演進為 120+ 微服務，涵蓋完整的遷移工具鏈和問題模式

**原文：** [infoq-main](https://www.infoq.com/articles/pull-based-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Article: The Hard-Stop Rule: From 3 HCM Monoliths to 120 Domain Microservices

A payroll and HR software team rebuilt three monoliths into over 120 smaller services over five years, with no dedicated migration budget. Every new feature was built as its own service instead of changing the old ones. The article covers the pull-based migration, the tools that made this possible, how costs were kept down, and the problems the team ran into along the way. By Prashanth Pasham

</details>