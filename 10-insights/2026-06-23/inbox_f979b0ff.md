---
id: inbox_f979b0ff
date: 2026-06-23
source_ref: "[[00-inbox/2026-06-23/2200-medium-tag-claude-orchestration-is-the-new-parameter-count-98bb]]"
title: "Orchestration Is the New Parameter Count — Fugu and the future of AI"
url: https://medium.com/@ChristopherMeredith/orchestration-is-the-new-parameter-count-fugu-and-the-future-of-ai-8fc31cc57695?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-06-23T20:32:40+00:00
fetched_at: 2026-06-23T22:15:27.283820+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章論證 AI 系統能力的新擴展軸線不再單純依賴模型參數規模，而是多個專家模型間的協調層（orchestration layer）。Sakana AI 的 Fugu 是一個 learned orchestrator，透過訓練而非規則庫來智能路由任務至專家模型，驗證輸出，並合成結果。相比傳統大模型擴展需要海量算力投資，協調層提供了更經濟的能力提升路徑——包括改進的路由決策、專家委派、驗證迴圈，以及供應商多元化的業務連續性。開發者應將協調層視為一級公民元件，從設計初期就融入提供商多元化和驗證機制。"
key_points:
  - "Fugu 採 learned orchestrator 設計：訓練系統學習最佳模型組合，非硬編碼規則"
  - "協調層提供供應商獨立性：單一提供商政策變化時可自動路由至替代方案，避免系統崩潰"
  - "相比單一大模型擴展，協調層擴展成本更低：無需新的海量訓練運行和基礎設施投資"
tags: [orchestration, multi-model-routing, learned-systems, fugu, ai-scaling]
topics: [foundation_models.claude]
importance: 4
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Orchestration Is the New Parameter Count — Fugu and the future of AI

文章論證 AI 系統能力的新擴展軸線不再單純依賴模型參數規模，而是多個專家模型間的協調層（orchestration layer）。Sakana AI 的 Fugu 是一個 learned orchestrator，透過訓練而非規則庫來智能路由任務至專家模型，驗證輸出，並合成結果。相比傳統大模型擴展需要海量算力投資，協調層提供了更經濟的能力提升路徑——包括改進的路由決策、專家委派、驗證迴圈，以及供應商多元化的業務連續性。開發者應將協調層視為一級公民元件，從設計初期就融入提供商多元化和驗證機制。

### 重點
- Fugu 採 learned orchestrator 設計：訓練系統學習最佳模型組合，非硬編碼規則
- 協調層提供供應商獨立性：單一提供商政策變化時可自動路由至替代方案，避免系統崩潰
- 相比單一大模型擴展，協調層擴展成本更低：無需新的海量訓練運行和基礎設施投資

**原文：** [medium-tag-claude](https://medium.com/@ChristopherMeredith/orchestration-is-the-new-parameter-count-fugu-and-the-future-of-ai-8fc31cc57695?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

For three years the playbook was simple: bigger model, better output. Continue reading on Medium »

</details>