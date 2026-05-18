---
id: inbox_914d8e4c
date: 2026-05-12
source_ref: "[[00-inbox/2026-05-12/1800-medium-towards-data-science-from-vibe-coding-to-spec-driven-developm-0c08]]"
title: "From Vibe Coding to Spec-Driven Development"
url: https://towardsdatascience.com/from-vibe-coding-to-spec-driven-development/
source: medium-towards-data-science
published_at: 2026-05-12T16:30:00+00:00
fetched_at: 2026-05-12T18:05:54.389375+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "從「vibe coding」轉向「spec-driven development」的產業轉變：工程師社區已認知 LLM 快速原型化的局限，Andrej Karpathy（vibe coding 創始人）本人於 1 年後承認該時代已終結，進入「agentic engineering」階段——即編排 agents 執行詳細規格、由人類提供監督。spec-driven development 與傳統工程更相近，強調在實裝前完成架構決策和需求文檔化，保存規格於版本控制倉庫，解決 vibe coding 的上下文衰減、缺乏共識慣例、決策遺忘等問題。文章以健身應用實踐為例，展示 4.5 小時從想法到工作應用的完整工程流程。"
key_points:
  - "Andrej Karpathy 承認「vibe coding」時代結束，轉向「agentic engineering」（99% 情況下不直接寫代碼，而是編排 agents + 人工監督）"
  - "Spec-driven development 預先完成架構決策、需求定義，規格文檔化存入版本控制，解決 vibe coding 的上下文衰減與決策追蹤問題"
  - "實踐案例：4.5 小時內透過規格驅動 LLM agents 構建跨 UI/後端的完整健身應用，無需手工調試迭代"
tags: [agentic-engineering, spec-driven-development, llm-agents, software-engineering, context-management]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## From Vibe Coding to Spec-Driven Development

從「vibe coding」轉向「spec-driven development」的產業轉變：工程師社區已認知 LLM 快速原型化的局限，Andrej Karpathy（vibe coding 創始人）本人於 1 年後承認該時代已終結，進入「agentic engineering」階段——即編排 agents 執行詳細規格、由人類提供監督。spec-driven development 與傳統工程更相近，強調在實裝前完成架構決策和需求文檔化，保存規格於版本控制倉庫，解決 vibe coding 的上下文衰減、缺乏共識慣例、決策遺忘等問題。文章以健身應用實踐為例，展示 4.5 小時從想法到工作應用的完整工程流程。

### 重點
- Andrej Karpathy 承認「vibe coding」時代結束，轉向「agentic engineering」（99% 情況下不直接寫代碼，而是編排 agents + 人工監督）
- Spec-driven development 預先完成架構決策、需求定義，規格文檔化存入版本控制，解決 vibe coding 的上下文衰減與決策追蹤問題
- 實踐案例：4.5 小時內透過規格驅動 LLM agents 構建跨 UI/後端的完整健身應用，無需手工調試迭代

**原文：** [medium-towards-data-science](https://towardsdatascience.com/from-vibe-coding-to-spec-driven-development/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A 4.5-hour journey from idea to working fitness app with LLM agents 
 The post From Vibe Coding to Spec-Driven Development appeared first on Towards Data Science .

</details>