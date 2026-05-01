---
id: inbox_fa1855ef
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/1257-medium-tag-llm-the-evolution-of-shared-language-in-ai-a-452b]]"
title: "The Evolution of Shared Language in AI Agent Development"
url: https://cobusgreyling.medium.com/the-evolution-of-shared-language-in-ai-agent-development-a51836b010eb?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-01T06:01:01+00:00
fetched_at: 2026-05-01T13:24:38.343166+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者梳理 AI agent 開發 6 年來的語言演變軌跡，從 2020-2022 年的 LLM 基礎概念（prompts、tokens）進化到 2025 年的協議標準化（MCP、CUA、A2A），再到 2026 年的「Harness 工程」新階段。核心轉變是從「agent 能做什麼」（能力導向）轉向「如何控制 agent 實際做什麼」（控制導向），強調 right-sizing（精準匹配模型能力與任務難度）而非盲目追求最大模型。這反映產業從實驗向工程實踐的成熟期轉變。"
key_points:
  - "6階段演變模型：LLM基礎→組件化(RAG)→智能體(Tool Calling)→多智能體編排(LangGraph)→協議互通(MCP、A2A)→Harness工程(控制層設計)"
  - "Harness工程的核心：系統提示、hooks、context管理等控制層設計，關鍵是「如何約束agent」而非「擴大agent能力」"
  - "Right-sizing原則：小、快、便宜的模型足以應對日常分類；複雜推理才需要大模型——成本與性能精準匹配優於盲目堆砌"
tags: [ai-agents, agent-development, mcp, harness-engineering, right-sizing]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## The Evolution of Shared Language in AI Agent Development

作者梳理 AI agent 開發 6 年來的語言演變軌跡，從 2020-2022 年的 LLM 基礎概念（prompts、tokens）進化到 2025 年的協議標準化（MCP、CUA、A2A），再到 2026 年的「Harness 工程」新階段。核心轉變是從「agent 能做什麼」（能力導向）轉向「如何控制 agent 實際做什麼」（控制導向），強調 right-sizing（精準匹配模型能力與任務難度）而非盲目追求最大模型。這反映產業從實驗向工程實踐的成熟期轉變。

### 重點
- 6階段演變模型：LLM基礎→組件化(RAG)→智能體(Tool Calling)→多智能體編排(LangGraph)→協議互通(MCP、A2A)→Harness工程(控制層設計)
- Harness工程的核心：系統提示、hooks、context管理等控制層設計，關鍵是「如何約束agent」而非「擴大agent能力」
- Right-sizing原則：小、快、便宜的模型足以應對日常分類；複雜推理才需要大模型——成本與性能精準匹配優於盲目堆砌

**原文：** [medium-tag-llm](https://cobusgreyling.medium.com/the-evolution-of-shared-language-in-ai-agent-development-a51836b010eb?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://cobusgreyling.medium.com/the-evolution-of-shared-language-in-ai-agent-development-a51836b010eb?source=rss------large_language_models-5"><img src="https://cdn-images-1.medium.com/max/1810/1*UT_47UW3MbaT4Sd3GxvVFw.png" width="1810" /></a></p><p class="medium-feed-snippet">Something interesting is happening in AI agent development&#x2026;</p><p class="medium-feed-link"><a href="https://cobusgreyling.medium.com/the-evolution-of-shared-language-in-ai-agent-development-a51836b010eb?source=rss------large_language_models-5">Continue reading on Medium »</a></p></div>

</details>