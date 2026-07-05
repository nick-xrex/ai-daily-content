---
id: inbox_a18b7a95
date: 2026-07-04
source_ref: "[[00-inbox/2026-07-04/2200-medium-tag-llm-your-context-window-is-the-bug-not-the-m-7724]]"
title: "Your Context Window Is the Bug, Not the Model"
url: https://medium.com/@sebuzdugan/your-context-window-is-the-bug-not-the-model-dd29e71ba977?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-07-04T15:05:08+00:00
fetched_at: 2026-07-04T22:10:29.691578+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文揭示 LLM agent 在不同 context window 大小下的性能差異：Agent 在 8K tokens 時表現正常，但當 context 增長至 60K tokens 時，開始出現工具呼叫幻覺 (hallucinating tool calls) 與上下文遺忘現象。文章主張問題的根源不在模型本身，而在於 context window 的管理與使用方式。這表明開發者在設計 agent 系統時，需要特別關注長文本場景下的 context 退化問題，而非單純依賴模型升級。"
key_points:
  - "Agent 在 8K tokens 正常運作，但在 60K tokens 時性能顯著崩壞"
  - "高 token 數下出現工具呼叫幻覺與上下文丟失"
  - "Context window 管理是 agent 可靠性的關鍵，比模型能力本身更影響系統表現"
tags: [context-window, agent-degradation, llm-reliability, token-limit]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Your Context Window Is the Bug, Not the Model

本文揭示 LLM agent 在不同 context window 大小下的性能差異：Agent 在 8K tokens 時表現正常，但當 context 增長至 60K tokens 時，開始出現工具呼叫幻覺 (hallucinating tool calls) 與上下文遺忘現象。文章主張問題的根源不在模型本身，而在於 context window 的管理與使用方式。這表明開發者在設計 agent 系統時，需要特別關注長文本場景下的 context 退化問題，而非單純依賴模型升級。

### 重點
- Agent 在 8K tokens 正常運作，但在 60K tokens 時性能顯著崩壞
- 高 token 數下出現工具呼叫幻覺與上下文丟失
- Context window 管理是 agent 可靠性的關鍵，比模型能力本身更影響系統表現

**原文：** [medium-tag-llm](https://medium.com/@sebuzdugan/your-context-window-is-the-bug-not-the-model-dd29e71ba977?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Your agent nails the demo at 8K tokens, then starts inventing tool calls and losing the thread at 60K. Continue reading on Medium »

</details>