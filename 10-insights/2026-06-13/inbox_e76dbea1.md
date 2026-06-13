---
id: inbox_e76dbea1
date: 2026-06-13
source_ref: "[[00-inbox/2026-06-13/2200-medium-tag-llm-your-ai-agent-re-reads-every-page-it-alr-4a5a]]"
title: "Your AI Agent Re-Reads Every Page It Already Saw. I Measured the 8x Context Tax"
url: https://medium.com/@spinov001/your-ai-agent-re-reads-every-page-it-already-saw-i-measured-the-8x-context-tax-8513678f8b29?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-13T18:49:22+00:00
fetched_at: 2026-06-13T22:09:06.801515+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "實測 AI 代理在多轉對話中的「上下文稅」現象：第 1 轉消耗約 300 個輸入 token，第 20 轉消耗 7,000 個，成本暴增 23 倍。問題根源在於每一轉中，AI 代理都重新讀取與處理所有既往的對話內容與頁面資料，導致上下文窗口持續膨脹。此發現對多轉互動應用（如 RAG、多步推理）的成本預算與系統設計有重要參考價值，凸顯了長對話型 Agent 的實務挑戰。"
key_points:
  - "多轉代理成本非線性增長：Turn 1 為 300 tokens，Turn 20 為 7,000 tokens（增長 23 倍）"
  - "根本原因：每轉代理重複讀取並重新處理全部歷史內容"
  - "長對話型 Agent 應用需重新評估 token 預算模型與成本結構"
tags: [context-window, token-cost, multi-turn-agents, inference-cost]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Your AI Agent Re-Reads Every Page It Already Saw. I Measured the 8x Context Tax

實測 AI 代理在多轉對話中的「上下文稅」現象：第 1 轉消耗約 300 個輸入 token，第 20 轉消耗 7,000 個，成本暴增 23 倍。問題根源在於每一轉中，AI 代理都重新讀取與處理所有既往的對話內容與頁面資料，導致上下文窗口持續膨脹。此發現對多轉互動應用（如 RAG、多步推理）的成本預算與系統設計有重要參考價值，凸顯了長對話型 Agent 的實務挑戰。

### 重點
- 多轉代理成本非線性增長：Turn 1 為 300 tokens，Turn 20 為 7,000 tokens（增長 23 倍）
- 根本原因：每轉代理重複讀取並重新處理全部歷史內容
- 長對話型 Agent 應用需重新評估 token 預算模型與成本結構

**原文：** [medium-tag-llm](https://medium.com/@spinov001/your-ai-agent-re-reads-every-page-it-already-saw-i-measured-the-8x-context-tax-8513678f8b29?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Turn 1 cost about 300 input tokens. Turn 20 cost 7,000. Same agent, same kind of page, 20 times more expensive for the last step than the&#x2026; Continue reading on Medium »

</details>