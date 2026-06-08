---
id: inbox_af04b883
date: 2026-06-07
source_ref: "[[00-inbox/2026-06-07/2346-medium-tag-llm-how-to-design-agent-memory-9d64]]"
title: "How to Design Agent Memory"
url: https://medium.com/@foks.wang/how-to-design-agent-memory-3a4a8f3be6b3?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-07T19:31:36+00:00
fetched_at: 2026-06-07T23:52:24.101447+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Agent 記憶系統設計超越「只用向量資料庫」的簡化認知。文章提出三層架構：(1) Working Memory（工作記憶）——最近對話、當前計劃、工具輸出直接存在上下文窗口；(2) Compressed Memory（壓縮記憶）——將舊交互摘要為結構化狀態（目標、完成步驟、約束、失敗嘗試）以管理上下文增長；(3) Long-Term Memory（長期記憶）——跨會話持久化存儲用戶偏好、專案事實、工作流程。核心洞察：記憶系統最重要的是「路由邏輯」（決定保留、壓縮、檢索、遺忘什麼），而非存儲本身。"
key_points:
  - "記憶三層架構：Working（上下文）→ Compressed（結構化摘要）→ Long-Term（資料庫）"
  - "核心是記憶路由，不是存儲——決定什麼保留、什麼遺忘、何時檢索"
  - "寫入策略最關鍵：區分臨時觀察 vs 可重用的永久知識；上下文污染（陳舊+無關資料）會降低推理效能"
tags: [agent-memory, context-management, memory-architecture, vector-database, knowledge-routing]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## How to Design Agent Memory

Agent 記憶系統設計超越「只用向量資料庫」的簡化認知。文章提出三層架構：(1) Working Memory（工作記憶）——最近對話、當前計劃、工具輸出直接存在上下文窗口；(2) Compressed Memory（壓縮記憶）——將舊交互摘要為結構化狀態（目標、完成步驟、約束、失敗嘗試）以管理上下文增長；(3) Long-Term Memory（長期記憶）——跨會話持久化存儲用戶偏好、專案事實、工作流程。核心洞察：記憶系統最重要的是「路由邏輯」（決定保留、壓縮、檢索、遺忘什麼），而非存儲本身。

### 重點
- 記憶三層架構：Working（上下文）→ Compressed（結構化摘要）→ Long-Term（資料庫）
- 核心是記憶路由，不是存儲——決定什麼保留、什麼遺忘、何時檢索
- 寫入策略最關鍵：區分臨時觀察 vs 可重用的永久知識；上下文污染（陳舊+無關資料）會降低推理效能

**原文：** [medium-tag-llm](https://medium.com/@foks.wang/how-to-design-agent-memory-3a4a8f3be6b3?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The fastest way to give a weak answer about agent memory is to say, &#x201c;Use a vector database.&#x201d;
That is not wrong, but it is incomplete. Continue reading on Medium »

</details>