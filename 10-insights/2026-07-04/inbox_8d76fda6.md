---
id: inbox_8d76fda6
date: 2026-07-04
source_ref: "[[00-inbox/2026-07-04/2200-medium-tag-llm-build-a-self-correcting-ai-agent-with-la-752c]]"
title: "Build a Self-Correcting AI Agent with LangGraph and Ollama"
url: https://generativeai.pub/build-a-self-correcting-ai-agent-with-langgraph-and-ollama-80c43f8f8f17?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-07-04T17:33:25+00:00
fetched_at: 2026-07-04T22:10:29.690064+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文展示如何使用 LangGraph 與 Ollama 搭建完全本地運行的自修正 AI Agent。核心架構為三層迴路：Generator → Critic → Adjudicator，由三個獨立的 Ollama 模型協作執行。系統使用結構化 JSON 評分標準進行品質檢查，透過條件路由根據評分結果決定是否重新生成或通過。這種設計有助於提高本地 LLM 應用的輸出品質，同時避免依賴商業 API。

```mermaid
graph LR
    Input[\"Input\"] --> Gen[\"Generator<br/>(Ollama Model 1)\"]
    Gen --> Output[\"Generated Output\"]
    Output --> Critic[\"Critic<br/>(Ollama Model 2)\"]
    Critic --> Score[\"Quality Score<br/>(JSON Rubric)\"]
    Score --> Adj[\"Adjudicator<br/>(Ollama Model 3)\"]
    Adj --> Decision{Quality<br/>Pass?}
    Decision -->|No| Gen
    Decision -->|Yes| Final[\"Final Output\"]
```"
key_points:
  - "Generator → Critic → Adjudicator 三層迴路，三個獨立 Ollama 模型協作"
  - "使用 structured JSON rubric 進行自動品質評分與條件路由"
  - "完全本地運行，不依賴外部 API，降低成本並保護隱私"
tags: [agent, langgraph, ollama, self-correction, local-llm]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Build a Self-Correcting AI Agent with LangGraph and Ollama

本文展示如何使用 LangGraph 與 Ollama 搭建完全本地運行的自修正 AI Agent。核心架構為三層迴路：Generator → Critic → Adjudicator，由三個獨立的 Ollama 模型協作執行。系統使用結構化 JSON 評分標準進行品質檢查，透過條件路由根據評分結果決定是否重新生成或通過。這種設計有助於提高本地 LLM 應用的輸出品質，同時避免依賴商業 API。

```mermaid
graph LR
    Input["Input"] --> Gen["Generator<br/>(Ollama Model 1)"]
    Gen --> Output["Generated Output"]
    Output --> Critic["Critic<br/>(Ollama Model 2)"]
    Critic --> Score["Quality Score<br/>(JSON Rubric)"]
    Score --> Adj["Adjudicator<br/>(Ollama Model 3)"]
    Adj --> Decision{Quality<br/>Pass?}
    Decision -->|No| Gen
    Decision -->|Yes| Final["Final Output"]
```

### 重點
- Generator → Critic → Adjudicator 三層迴路，三個獨立 Ollama 模型協作
- 使用 structured JSON rubric 進行自動品質評分與條件路由
- 完全本地運行，不依賴外部 API，降低成本並保護隱私

**原文：** [medium-tag-llm](https://generativeai.pub/build-a-self-correcting-ai-agent-with-langgraph-and-ollama-80c43f8f8f17?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A fully local Generator &#x2192; Critic &#x2192; Adjudicator loop: three Ollama models, a structured JSON rubric, conditional routing, and a quality bar&#x2026; Continue reading on Generative AI »

</details>