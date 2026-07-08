---
id: inbox_ff615147
date: 2026-07-07
source_ref: "[[00-inbox/.../inbox_ff615147]]"
title: "Presentation: Designing AI Platforms for Reliability: Tools for Certainty, Agents for Discovery"
url: https://www.infoq.com/presentations/reliable-ai-platforms/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-07T08:03:00+00:00
fetched_at: 2026-07-08T01:06:17.434510+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "NVIDIA 工程師 Aaron Erickson 發表演講，闡述設計可靠 AI 平台的核心原則：明確分工「工具負責確定性、代理負責探索」。演講揭示了三個關鍵實踐：(1) 利用稀缺上下文（rare context）優化模型輸入；(2) 建立 LLM-as-a-judge 測試金字塔以確保代理決策品質；(3) 通過限制選項數量避免「選擇悖論」導致的代理性能下降。此框架特別適合需要在成本、延遲和準確度間平衡的生產級系統。"
key_points:
  - "工具（deterministic tools）用於高確定性路徑，代理（agents）用於探索性任務——此分工可大幅提升系統可靠性"
  - "LLM-as-a-judge 測試金字塔是驗證代理層級決策品質的標準框架"
  - "稀缺上下文（rare context）利用和選擇悖論規避是代理可靠性的兩大優化維度"
tags: [ai-reliability, agent-hierarchy, llm-as-judge, production-ai-systems]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Designing AI Platforms for Reliability: Tools for Certainty, Agents for Discovery

NVIDIA 工程師 Aaron Erickson 發表演講，闡述設計可靠 AI 平台的核心原則：明確分工「工具負責確定性、代理負責探索」。演講揭示了三個關鍵實踐：(1) 利用稀缺上下文（rare context）優化模型輸入；(2) 建立 LLM-as-a-judge 測試金字塔以確保代理決策品質；(3) 通過限制選項數量避免「選擇悖論」導致的代理性能下降。此框架特別適合需要在成本、延遲和準確度間平衡的生產級系統。

### 重點
- 工具（deterministic tools）用於高確定性路徑，代理（agents）用於探索性任務——此分工可大幅提升系統可靠性
- LLM-as-a-judge 測試金字塔是驗證代理層級決策品質的標準框架
- 稀缺上下文（rare context）利用和選擇悖論規避是代理可靠性的兩大優化維度

**原文：** [infoq-main](https://www.infoq.com/presentations/reliable-ai-platforms/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Presentation: Designing AI Platforms for Reliability: Tools for Certainty, Agents for Discovery

Aaron Erickson explains how NVIDIA designs and tests purpose-built AI agent hierarchies. For senior developers and architects, he outlines why balancing deterministic tools with agentic discovery is crucial. Discover how to leverage rare context, implement LLM-as-a-judge test pyramids, and avoid the paradox of choice to build highly reliable, production-grade AI systems at scale. By Aaron Erickson

</details>