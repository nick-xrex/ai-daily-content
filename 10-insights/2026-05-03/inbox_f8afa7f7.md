---
id: inbox_f8afa7f7
date: 2026-05-03
source_ref: "[[00-inbox/2026-05-03/0131-medium-tag-ai-5-things-i-wish-i-knew-before-building-a-d644]]"
title: "5 Things I Wish I Knew Before Building Autonomous Systems"
url: https://medium.com/@GaurangGhadi/5-things-i-wish-i-knew-before-building-autonomous-systems-a6aca177faf6?source=rss------artificial_intelligence-5
source: medium-tag-ai
published_at: 2026-05-03T00:36:26+00:00
fetched_at: 2026-05-03T01:46:29.679483+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者分享開發自主系統的 5 個核心教訓：(1) 獎勵函數必須明確且激進設計，否則代理無法感知目標差異；(2) 模擬與現實存在必然差距（馬達延遲、氣流、非高斯噪聲），需接受模擬僅為起點，採域隨機化建立魯棒性；(3) 採用感知→規劃→控制模組化管道優於端到端黑盒模型，利於精確除錯；(4) 線性 Q 學習與線性 SARSA 等簡單算法常比 DQN 等複雜方法提供更低方差與更好一致性；(5) 深入理解算法內部機制（數值量級、計算流程）比調參數更快解決問題。核心主題為實踐經驗優於理論推測。"
key_points:
  - "獎勵函數權重必須設計得足夠激進，使代理『感受到』目標差異，tiny multiplier 無法驅動行為改變"
  - "模擬到現實的轉移失敗不可避免，需採域隨機化策略建立魯棒性，將模擬視為起點而非終點"
  - "模組化架構（感知→規劃→控制）比端到端學習更便於除錯，可精確定位故障子系統"
tags: [reinforcement-learning, autonomous-systems, sim-to-real, reward-design, modular-architecture]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## 5 Things I Wish I Knew Before Building Autonomous Systems

作者分享開發自主系統的 5 個核心教訓：(1) 獎勵函數必須明確且激進設計，否則代理無法感知目標差異；(2) 模擬與現實存在必然差距（馬達延遲、氣流、非高斯噪聲），需接受模擬僅為起點，採域隨機化建立魯棒性；(3) 採用感知→規劃→控制模組化管道優於端到端黑盒模型，利於精確除錯；(4) 線性 Q 學習與線性 SARSA 等簡單算法常比 DQN 等複雜方法提供更低方差與更好一致性；(5) 深入理解算法內部機制（數值量級、計算流程）比調參數更快解決問題。核心主題為實踐經驗優於理論推測。

### 重點
- 獎勵函數權重必須設計得足夠激進，使代理『感受到』目標差異，tiny multiplier 無法驅動行為改變
- 模擬到現實的轉移失敗不可避免，需採域隨機化策略建立魯棒性，將模擬視為起點而非終點
- 模組化架構（感知→規劃→控制）比端到端學習更便於除錯，可精確定位故障子系統

**原文：** [medium-tag-ai](https://medium.com/@GaurangGhadi/5-things-i-wish-i-knew-before-building-autonomous-systems-a6aca177faf6?source=rss------artificial_intelligence-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@GaurangGhadi/5-things-i-wish-i-knew-before-building-autonomous-systems-a6aca177faf6?source=rss------artificial_intelligence-5"><img src="https://cdn-images-1.medium.com/max/759/1*d6DPMjyChscHgk3W3bJ_7A.png" width="759" /></a></p><p class="medium-feed-snippet">I&#x2019;m not going to explain what a robot is. If you&#x2019;re here, you already know. You&#x2019;ve probably broken something expensive. Had the moment&#x2026;</p><p class="medium-feed-link"><a href="https://medium.com/@GaurangGhadi/5-things-i-wish-i-knew-before-building-autonomous-systems-a6aca177faf6?source=rss------artificial_intelligence-5">Continue reading on Medium »</a></p></div>

</details>