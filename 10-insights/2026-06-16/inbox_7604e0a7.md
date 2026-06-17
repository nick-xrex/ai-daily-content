---
id: inbox_7604e0a7
date: 2026-06-16
source_ref: "[[00-inbox/2026-06-16/2200-infoq-main-coinbase-postmortem-reveals-how-a-locali-12b7]]"
title: "Coinbase Postmortem Reveals How a Localized AWS Failure Triggered a Multi-Hour Trading Outage"
url: https://www.infoq.com/news/2026/06/coinbase-aws-failure-postmortem/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-16T12:00:00+00:00
fetched_at: 2026-06-16T22:10:50.869428+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Coinbase 於六月發佈其五月七日停機事件的詳細事後分析。本次事件始於 AWS 某數據中心的局部冷卻系統故障，導致設備過熱。故障迅速級聯擴散，影響多個相互依賴的系統，最終造成 Coinbase 幾乎全部交易功能癱瘓，持續多小時。該事件對整個交易所用戶造成嚴重影響，無法進行任何交易活動。事後分析深刻揭示了依賴單一雲供應商單一區域的風險。此事件強調多區域部署和自主故障轉移機制的關鍵重要性。"
key_points:
  - "AWS 單一數據中心冷卻故障導致硬體過熱與級聯故障擴散"
  - "交易停運持續數小時，影響 Coinbase 全部交易功能"
  - "暴露單一區域依賴的風險與多區域冗餘設計的必要性"
tags: [aws-outage, infrastructure, resilience, failure-cascade, postmortem]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Coinbase Postmortem Reveals How a Localized AWS Failure Triggered a Multi-Hour Trading Outage

Coinbase 於六月發佈其五月七日停機事件的詳細事後分析。本次事件始於 AWS 某數據中心的局部冷卻系統故障，導致設備過熱。故障迅速級聯擴散，影響多個相互依賴的系統，最終造成 Coinbase 幾乎全部交易功能癱瘓，持續多小時。該事件對整個交易所用戶造成嚴重影響，無法進行任何交易活動。事後分析深刻揭示了依賴單一雲供應商單一區域的風險。此事件強調多區域部署和自主故障轉移機制的關鍵重要性。

### 重點
- AWS 單一數據中心冷卻故障導致硬體過熱與級聯故障擴散
- 交易停運持續數小時，影響 Coinbase 全部交易功能
- 暴露單一區域依賴的風險與多區域冗餘設計的必要性

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/coinbase-aws-failure-postmortem/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Coinbase has published a detailed postmortem of its May 7, 2026, outage, revealing how a localized cooling failure inside an AWS data center escalated into a multi-hour disruption that halted nearly all trading activity across the cryptocurrency exchange By Craig Risi

</details>