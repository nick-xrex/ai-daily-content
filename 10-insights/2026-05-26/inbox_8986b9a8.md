---
id: inbox_8986b9a8
date: 2026-05-26
source_ref: "[[00-inbox/2026-05-26/0023-substack-bytebytego-how-vercel-cut-build-wait-times-from-90-f878]]"
title: "How Vercel Cut Build Wait Times From 90 Seconds To 5"
url: https://blog.bytebytego.com/p/how-vercel-cut-build-wait-times-from
source: substack-bytebytego
published_at: 2026-05-26T15:31:10+00:00
fetched_at: 2026-05-27T00:35:59.753715+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Vercel 於 2023 年 11 月推出內部平台 Hive，將構建時間從 90 秒削減至 5 秒，達成 18 倍加速。這不單純是性能優化故事，而是透過接受更嚴格約束、構築更複雜基礎、堆疊三層優化而達成。Vercel 的核心假設：每段執行代碼可能是惡意的（敵對多租戶），運行在與其他客戶共享的硬體上。此假設徹底改變基礎設施的信任模型 — 從「己方代碼在己方伺服器」的協作模式，轉變為「陌生人代碼在共享硬體」的對抗模式。標準容器與 Kubernetes 設計面向協作工作負載，無法提供必要的對抗隔離；Hive 需從原始層面構築硬化隔離機制，超越標準 Docker/Kubernetes。該案例展示在多租戶環保下，基礎假設如何驅動架構決策與優化策略的深層改造。"
key_points:
  - "Hive 平台成績：構建時間 90s → 5s（18 倍加速），透過三層優化達成"
  - "敵對多租戶假設改造信任模型：從協作工作負載的「機器信任代碼」翻轉為對抗隔離的「平台防禦代碼」"
  - "容器硬化超越標準 Docker/Kubernetes：單一核心漏洞可洩露全機客戶數據，Vercel 需自製隔離機制"
tags: [infrastructure, platform-architecture, build-optimization, multi-tenancy]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## How Vercel Cut Build Wait Times From 90 Seconds To 5

Vercel 於 2023 年 11 月推出內部平台 Hive，將構建時間從 90 秒削減至 5 秒，達成 18 倍加速。這不單純是性能優化故事，而是透過接受更嚴格約束、構築更複雜基礎、堆疊三層優化而達成。Vercel 的核心假設：每段執行代碼可能是惡意的（敵對多租戶），運行在與其他客戶共享的硬體上。此假設徹底改變基礎設施的信任模型 — 從「己方代碼在己方伺服器」的協作模式，轉變為「陌生人代碼在共享硬體」的對抗模式。標準容器與 Kubernetes 設計面向協作工作負載，無法提供必要的對抗隔離；Hive 需從原始層面構築硬化隔離機制，超越標準 Docker/Kubernetes。該案例展示在多租戶環保下，基礎假設如何驅動架構決策與優化策略的深層改造。

### 重點
- Hive 平台成績：構建時間 90s → 5s（18 倍加速），透過三層優化達成
- 敵對多租戶假設改造信任模型：從協作工作負載的「機器信任代碼」翻轉為對抗隔離的「平台防禦代碼」
- 容器硬化超越標準 Docker/Kubernetes：單一核心漏洞可洩露全機客戶數據，Vercel 需自製隔離機制

**原文：** [substack-bytebytego](https://blog.bytebytego.com/p/how-vercel-cut-build-wait-times-from)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

In this article, we examine the constraints Vercel faced, the choices they made in response, and the optimizations that produced the speedup.

</details>