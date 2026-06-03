---
id: inbox_3ed1a0d2
date: 2026-06-02
source_ref: "[[00-inbox/2026-06-02/0030-medium-tag-llm-long-term-agentic-memory-with-langgraph-1594]]"
title: "Long-Term Agentic Memory With LangGraph: Building AI Agents That Remember"
url: https://medium.com/@kumar.niranjan/long-term-agentic-memory-with-langgraph-building-ai-agents-that-remember-148cc8cf896e?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-02T18:07:46+00:00
fetched_at: 2026-06-03T00:41:54.166127+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LangGraph 透過三層記憶系統 (短期 context、長期偏好與歷史、檢索層) 實現 agent 跨會話持久化記憶。架構設計將圖節點對應推理步驟、工具執行、記憶操作、決策流程。執行流：用戶請求 → agent 查詢記憶庫 → 檢索相關資訊注入推理 → 執行動作 → 關鍵結果存回記憶。區分語義 (事實)、情節 (經驗)、程序性 (學習過程) 三類記憶，確保不同訊息類型的精準檢索。"
key_points:
  - "三層記憶架構：短期 (會話狀態) + 長期 (用戶偏好、歷史) + 檢索層 (前置搜尋)"
  - "語義/情節/程序性分類：針對不同記憶型態設計儲存與檢索策略"
  - "記憶即基礎設施：視為生產級 AI 系統核心而非可選功能；持續學習迴圈保持 up-to-date"
tags: [langgraph, agent-memory, long-term-memory, persistent-context]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Long-Term Agentic Memory With LangGraph: Building AI Agents That Remember

LangGraph 透過三層記憶系統 (短期 context、長期偏好與歷史、檢索層) 實現 agent 跨會話持久化記憶。架構設計將圖節點對應推理步驟、工具執行、記憶操作、決策流程。執行流：用戶請求 → agent 查詢記憶庫 → 檢索相關資訊注入推理 → 執行動作 → 關鍵結果存回記憶。區分語義 (事實)、情節 (經驗)、程序性 (學習過程) 三類記憶，確保不同訊息類型的精準檢索。

### 重點
- 三層記憶架構：短期 (會話狀態) + 長期 (用戶偏好、歷史) + 檢索層 (前置搜尋)
- 語義/情節/程序性分類：針對不同記憶型態設計儲存與檢索策略
- 記憶即基礎設施：視為生產級 AI 系統核心而非可選功能；持續學習迴圈保持 up-to-date

**原文：** [medium-tag-llm](https://medium.com/@kumar.niranjan/long-term-agentic-memory-with-langgraph-building-ai-agents-that-remember-148cc8cf896e?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Introduction Continue reading on Medium »

</details>