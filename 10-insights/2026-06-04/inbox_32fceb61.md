---
id: inbox_32fceb61
date: 2026-06-04
source_ref: "[[00-inbox/2026-06-04/0041-infoq-architecture-30-updates-per-second-per-account-uber-s-ef96]]"
title: "30+ Updates per Second per Account: Uber Scales Ledger Processing with Batching"
url: https://www.infoq.com/news/2026/06/uber-payment-batching-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-04T14:02:00+00:00
fetched_at: 2026-06-05T00:49:39.396095+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 開發高效能金融帳本處理系統，採用 250ms 批處理、Redis 協調和樂觀原子性更新機制，在分散式會計基礎設施中支援每個帳戶 30+ 次更新/秒，同時保證資料一致性和審計可追溯性。系統將原有的多小時處理管道壓縮至分鐘級。這是應對分散環境中「寫熱點」(hot account write contention) 的典範方案，結合批處理窗口與樂觀鎖策略有效突破吞吐量瓶頸。"
key_points:
  - "250ms 批處理窗口 + Redis 協調實現 30+ 更新/秒的單帳戶吞吐量"
  - "樂觀原子性更新保證一致性同時避免分散鎖開銷"
  - "多小時管道縮短至分鐘級，直接提升金融結算效率"
tags: [distributed-systems, financial-ledger, high-throughput-batching, uber-infrastructure]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## 30+ Updates per Second per Account: Uber Scales Ledger Processing with Batching

Uber 開發高效能金融帳本處理系統，採用 250ms 批處理、Redis 協調和樂觀原子性更新機制，在分散式會計基礎設施中支援每個帳戶 30+ 次更新/秒，同時保證資料一致性和審計可追溯性。系統將原有的多小時處理管道壓縮至分鐘級。這是應對分散環境中「寫熱點」(hot account write contention) 的典範方案，結合批處理窗口與樂觀鎖策略有效突破吞吐量瓶頸。

### 重點
- 250ms 批處理窗口 + Redis 協調實現 30+ 更新/秒的單帳戶吞吐量
- 樂觀原子性更新保證一致性同時避免分散鎖開銷
- 多小時管道縮短至分鐘級，直接提升金融結算效率

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/06/uber-payment-batching-system/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Uber introduced a high-throughput financial ledger processing system designed to handle hot account write contention at scale. Using 250ms batching, Redis coordination, and optimistic atomic updates, the system supports 30+ updates per second per account while preserving consistency and auditability, reducing multi-hour processing pipelines to minutes in its distributed accounting infrastructure. By Leela Kumili

</details>