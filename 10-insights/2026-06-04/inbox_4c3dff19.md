---
id: inbox_4c3dff19
date: 2026-06-04
source_ref: "[[00-inbox/.../inbox_4c3dff19]]"
title: "Presentation: Architecting a Centralized Platform for Data Deletion at Netflix"
url: https://www.infoq.com/presentations/architecting-deletion-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-04T10:26:00+00:00
fetched_at: 2026-06-05T01:16:26.811914+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Netflix 分享中央化數據刪除平台的架構設計，重點解決分散式資料存儲中的安全刪除挑戰。講者討論如何在保持耐久性、可用性和正確性間取得平衡，實現跨多個系統的刪除傳播，同時不影響線上流量。關鍵經驗包括控制墓碑（tombstone）積累、建立連續審計迴圈、以及通過中央化平台獲得組織信任。"
key_points:
  - "墓碑積累控制：防止刪除記錄在系統中無限增長，影響性能"
  - "連續審計迴圈：確保刪除操作的正確性和可追蹤性"
  - "無侵擾性傳播：多系統刪除協調不中斷線上流量"
tags: [data-deletion, distributed-systems, architecture, netflix]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## Presentation: Architecting a Centralized Platform for Data Deletion at Netflix

Netflix 分享中央化數據刪除平台的架構設計，重點解決分散式資料存儲中的安全刪除挑戰。講者討論如何在保持耐久性、可用性和正確性間取得平衡，實現跨多個系統的刪除傳播，同時不影響線上流量。關鍵經驗包括控制墓碑（tombstone）積累、建立連續審計迴圈、以及通過中央化平台獲得組織信任。

### 重點
- 墓碑積累控制：防止刪除記錄在系統中無限增長，影響性能
- 連續審計迴圈：確保刪除操作的正確性和可追蹤性
- 無侵擾性傳播：多系統刪除協調不中斷線上流量

**原文：** [infoq-main](https://www.infoq.com/presentations/architecting-deletion-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Presentation: Architecting a Centralized Platform for Data Deletion at Netflix

The speakers discuss the architectural challenges of executing safe data deletion across distributed datastores. Balancing durability, availability & correctness, they explain how to orchestrate multi-system deletion propagation without impacting live traffic. They share lessons on controlling tombstone accumulation, building continuous audit loops, and gaining trust with a centralized platform. By Vidhya Arvind, Shawn Liu

</details>