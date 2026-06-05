---
id: inbox_3c6a35d4
date: 2026-06-04
source_ref: "[[00-inbox/2026-06-04/0041-infoq-architecture-presentation-architecting-a-centralized-58f2]]"
title: "Presentation: Architecting a Centralized Platform for Data Deletion at Netflix"
url: https://www.infoq.com/presentations/architecting-deletion-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-04T10:26:00+00:00
fetched_at: 2026-06-05T00:49:39.407719+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Netflix 分享跨分散資料存儲系統進行安全資料刪除的架構設計經驗。系統需在耐久性、可用性與正確性之間權衡，採用中央化平台統一協調多系統刪除傳播，避免直播流量受影響。團隊分享了 tombstone 積累控制、連續審計循環建立、以及與組織間信任建立等核心經驗，展示大規模分散系統中「刪除承諾」的複雜性與解決方案。"
key_points:
  - "中央化平台協調多系統刪除傳播，防止實時流量中斷"
  - "Tombstone 控制機制避免元資料無限積累"
  - "連續審計循環與信任機制確保刪除完整性"
tags: [data-deletion, distributed-systems, netflix-architecture, data-governance]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Architecting a Centralized Platform for Data Deletion at Netflix

Netflix 分享跨分散資料存儲系統進行安全資料刪除的架構設計經驗。系統需在耐久性、可用性與正確性之間權衡，採用中央化平台統一協調多系統刪除傳播，避免直播流量受影響。團隊分享了 tombstone 積累控制、連續審計循環建立、以及與組織間信任建立等核心經驗，展示大規模分散系統中「刪除承諾」的複雜性與解決方案。

### 重點
- 中央化平台協調多系統刪除傳播，防止實時流量中斷
- Tombstone 控制機制避免元資料無限積累
- 連續審計循環與信任機制確保刪除完整性

**原文：** [infoq-architecture](https://www.infoq.com/presentations/architecting-deletion-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The speakers discuss the architectural challenges of executing safe data deletion across distributed datastores. Balancing durability, availability & correctness, they explain how to orchestrate multi-system deletion propagation without impacting live traffic. They share lessons on controlling tombstone accumulation, building continuous audit loops, and gaining trust with a centralized platform. By Vidhya Arvind, Shawn Liu

</details>