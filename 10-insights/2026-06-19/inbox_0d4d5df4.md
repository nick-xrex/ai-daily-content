---
id: inbox_0d4d5df4
date: 2026-06-19
source_ref: "[[00-inbox/2026-06-19/2200-infoq-architecture-behind-the-scenes-block-450-jvm-reposito-1623]]"
title: "Behind the Scenes: Block 450 JVM Repositories Into Monorepo to Reduce Dependency Drift"
url: https://www.infoq.com/news/2026/06/block-450-jvm-monorepo-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-19T14:47:00+00:00
fetched_at: 2026-06-19T22:14:33.375032+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Block Inc 將旗下 Cash App 和 Square 的約 450 個 JVM 儲存庫遷移至單一儲存庫，以減少依賴漂移和協調成本。該系統支持每週約 8,800 次構建，CI 時間 p90 為 10 分鐘。遷移通過基於依賴圖的構建、選擇性 CI 和自訂 IDE 工具，改善了跨服務變更協作、構建可見性和開發人員體驗。"
key_points:
  - "~450 個 JVM 儲存庫合併至單一儲存庫；每週構建 ~8,800 次；p90 CI 時間 ~10 分鐘"
  - "基於依賴圖驅動的選擇性構建優化，減少無謂的 CI 執行"
  - "通過單一儲存庫視圖改善跨服務變更協作和依賴漂移管理"
tags: [monorepo, jvm, cash-app, ci-optimization, dependency-management]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Behind the Scenes: Block 450 JVM Repositories Into Monorepo to Reduce Dependency Drift

Block Inc 將旗下 Cash App 和 Square 的約 450 個 JVM 儲存庫遷移至單一儲存庫，以減少依賴漂移和協調成本。該系統支持每週約 8,800 次構建，CI 時間 p90 為 10 分鐘。遷移通過基於依賴圖的構建、選擇性 CI 和自訂 IDE 工具，改善了跨服務變更協作、構建可見性和開發人員體驗。

### 重點
- ~450 個 JVM 儲存庫合併至單一儲存庫；每週構建 ~8,800 次；p90 CI 時間 ~10 分鐘
- 基於依賴圖驅動的選擇性構建優化，減少無謂的 CI 執行
- 通過單一儲存庫視圖改善跨服務變更協作和依賴漂移管理

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/06/block-450-jvm-monorepo-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Block, Inc. describes migrating ~450 JVM repositories into a monorepo across Cash App and Square engineering to reduce dependency drift and coordination overhead. The system supports ~8,800 weekly builds with ~10 min p90 CI time. The approach improves cross-service changes, build visibility, and developer experience through dependency graph–based builds, selective CI, and custom IDE tooling. By Leela Kumili

</details>