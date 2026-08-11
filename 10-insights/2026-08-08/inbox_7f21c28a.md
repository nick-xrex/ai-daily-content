---
id: inbox_7f21c28a
date: 2026-08-08
source_ref: "[[00-inbox/.../inbox_7f21c28a]]"
title: "Presentation: Keeping ChatGPT Fast as AI Development Accelerates"
url: https://www.infoq.com/presentations/openai-performance-engineering-agentic-coding/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-08-08T09:00:00+00:00
fetched_at: 2026-08-11T01:35:03.361059+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 工程師 Martin Spier 在 InfoQ 演講中分析代理工作流對 ChatGPT 產品性能的隱藏成本。代理自動化大幅增加代碼變更量，引發 GPU 外的系統瓶頸（編譯、測試、部署延遲）。OpenAI 部署常運行的 AI 代理自動化性能分析、回歸檢測與持續優化，形成「用代理監控代理」的反饋迴圈。此方案維持全球規模產品速度與可擴展性，展示 agentic workflow 時代對基礎設施的新要求。"
key_points:
  - "Agentic workflow 增加代碼變更量，但引發非 GPU 部分回歸（編譯、測試、部署延遲），需要專用監控基礎設施"
  - "OpenAI 用常運行 AI 代理自動化性能分析與回歸檢測，形成代理監控代理的反饋系統"
  - "全球規模 ChatGPT 部署隨開發加速而動態優化性能，傳統靜態監控不足"
tags: [agentic-workflows, performance-engineering, openai, continuous-optimization, code-generation]
topics: [foundation_models.gpt]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Keeping ChatGPT Fast as AI Development Accelerates

OpenAI 工程師 Martin Spier 在 InfoQ 演講中分析代理工作流對 ChatGPT 產品性能的隱藏成本。代理自動化大幅增加代碼變更量，引發 GPU 外的系統瓶頸（編譯、測試、部署延遲）。OpenAI 部署常運行的 AI 代理自動化性能分析、回歸檢測與持續優化，形成「用代理監控代理」的反饋迴圈。此方案維持全球規模產品速度與可擴展性，展示 agentic workflow 時代對基礎設施的新要求。

### 重點
- Agentic workflow 增加代碼變更量，但引發非 GPU 部分回歸（編譯、測試、部署延遲），需要專用監控基礎設施
- OpenAI 用常運行 AI 代理自動化性能分析與回歸檢測，形成代理監控代理的反饋系統
- 全球規模 ChatGPT 部署隨開發加速而動態優化性能，傳統靜態監控不足

**原文：** [infoq-main](https://www.infoq.com/presentations/openai-performance-engineering-agentic-coding/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Presentation: Keeping ChatGPT Fast as AI Development Accelerates

Martin Spier explains how agentic workflows dramatically increase code change volume at OpenAI. He discusses the hidden systemic performance costs of rapid shipping beyond GPUs, and shares how deploying always-on AI agents automates profiling, regression detection, and continuous optimization to maintain product speed and scalability at massive global scale. By Martin Spier

</details>