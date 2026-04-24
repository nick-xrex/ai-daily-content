---
id: inbox_7b47859a
date: 2026-04-23
source_ref: "[[00-inbox/2026-04-23/0246-infoq-main-presentation-how-to-build-an-exchange-su-fe5f]]"
title: "Presentation: How to Build an Exchange: Sub Millisecond Response Times and 24/7 Uptimes in the Cloud"
url: https://www.infoq.com/presentations/exchange-systems-cloud/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-04-23T09:29:00+00:00
fetched_at: 2026-04-24T03:00:09.880975+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Coinbase 採用單執行緒架構搭配 Raft 共識演算法，在雲端環境維持 24/7 可用性與亞毫秒級回應時間。決定論設計支援零停機滾動部署，並能完美重現生產日誌進行故障診斷。此架構簡化了系統複雜性，減少分散式系統帶來的故障面。金融交易所需要絕對可靠性和卓越效能，該設計很好地平衡了兩者。單執行緒模型相比複雜的分散式系統更易於驗證和除錯。"
key_points:
  - "單執行緒 + Raft 共識演算法實現高可用性與亞毫秒延遲"
  - "決定論設計支援零停機部署和完美日誌重現，簡化除錯流程"
  - "架構簡化性帶來可靠性優勢，減少故障面與驗證複雜度"
tags: [exchange-systems, single-threaded-architecture, raft-consensus, zero-downtime-deployment, determinism]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: How to Build an Exchange: Sub Millisecond Response Times and 24/7 Uptimes in the Cloud

Coinbase 採用單執行緒架構搭配 Raft 共識演算法，在雲端環境維持 24/7 可用性與亞毫秒級回應時間。決定論設計支援零停機滾動部署，並能完美重現生產日誌進行故障診斷。此架構簡化了系統複雜性，減少分散式系統帶來的故障面。金融交易所需要絕對可靠性和卓越效能，該設計很好地平衡了兩者。單執行緒模型相比複雜的分散式系統更易於驗證和除錯。

### 重點
- 單執行緒 + Raft 共識演算法實現高可用性與亞毫秒延遲
- 決定論設計支援零停機部署和完美日誌重現，簡化除錯流程
- 架構簡化性帶來可靠性優勢，減少故障面與驗證複雜度

**原文：** [infoq-main](https://www.infoq.com/presentations/exchange-systems-cloud/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/presentations/exchange-systems-cloud/en/mediumimage/frank-yu-medium-1776173818222.jpeg" /><p>Frank Yu shares Coinbase’s engineering philosophy for building resilient, fair, and fast financial exchanges. He explains the power of a single-threaded architecture combined with the Raft consensus algorithm to maintain 24/7 availability.  He discusses how determinism enables zero-downtime rolling deployments and the ability to replay production logs for perfect bug reproduction.</p> <i>By Frank Yu</i>

</details>