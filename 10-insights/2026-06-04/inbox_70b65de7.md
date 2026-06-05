---
id: inbox_70b65de7
date: 2026-06-04
source_ref: "[[00-inbox/.../inbox_70b65de7]]"
title: "30+ Updates per Second per Account: Uber Scales Ledger Processing with Batching"
url: https://www.infoq.com/news/2026/06/uber-payment-batching-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-04T14:02:00+00:00
fetched_at: 2026-06-05T01:15:46.255431+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 推出高吞吐分散式財務分類帳系統，採用 250ms 批次視窗、Redis 協調和樂觀原子更新，達成每帳戶 30+ 更新/秒，同時保留強一致性和完整可審計軌跡。系統將原本耗時數小時的多道會計處理管道縮減至分鐘級，大幅降低分散式帳務基礎設施延遲。"
key_points:
  - "250ms 批次視窗 + Redis 協調解決熱帳戶寫入爭用，達 30+ updates/sec/account"
  - "樂觀原子更新模式保留強一致性和完整可審計性"
  - "處理延遲劇減：從多小時級管道降至分鐘級"
tags: [uber, distributed-ledger, batching, redis, atomic-updates]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## 30+ Updates per Second per Account: Uber Scales Ledger Processing with Batching

Uber 推出高吞吐分散式財務分類帳系統，採用 250ms 批次視窗、Redis 協調和樂觀原子更新，達成每帳戶 30+ 更新/秒，同時保留強一致性和完整可審計軌跡。系統將原本耗時數小時的多道會計處理管道縮減至分鐘級，大幅降低分散式帳務基礎設施延遲。

### 重點
- 250ms 批次視窗 + Redis 協調解決熱帳戶寫入爭用，達 30+ updates/sec/account
- 樂觀原子更新模式保留強一致性和完整可審計性
- 處理延遲劇減：從多小時級管道降至分鐘級

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/uber-payment-batching-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# 30+ Updates per Second per Account: Uber Scales Ledger Processing with Batching

Uber introduced a high-throughput financial ledger processing system designed to handle hot account write contention at scale. Using 250ms batching, Redis coordination, and optimistic atomic updates, the system supports 30+ updates per second per account while preserving consistency and auditability, reducing multi-hour processing pipelines to minutes in its distributed accounting infrastructure. By Leela Kumili

</details>