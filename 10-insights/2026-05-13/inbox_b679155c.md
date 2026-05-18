---
id: inbox_b679155c
date: 2026-05-13
source_ref: "[[00-inbox/.../inbox_b679155c]]"
title: "Presentation: What I Learned Building Multi-Agent Systems From Scratch"
url: https://www.infoq.com/presentations/multi-agent-system-lessons/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-05-13T12:01:00+00:00
fetched_at: 2026-05-18T03:34:53.084735+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Shopify 分享多 agents 系統建構經驗。從簡單聊天工具演進至專門化 agents 群，架構轉變為精簡、窄焦點的 agent 微服務，任務時間從小時級降至分鐘級。提出未來假說：檔案系統適配器可解決 context bloat，為大規模 agent 編排提供參考。"
key_points:
  - "架構演進：全能型 prompts → 專門化 agent 微服務（task time: 小時 → 分鐘）"
  - "窄焦點設計降低 context 負擔，提升執行效率"
  - "未來方向：檔案系統適配器解決 context bloat，提升可擴展性"
tags: [multi-agent-systems, system-design, shopify, context-management, agent-architecture]
topics: []
importance: 4
novelty: 3
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: What I Learned Building Multi-Agent Systems From Scratch

Shopify 分享多 agents 系統建構經驗。從簡單聊天工具演進至專門化 agents 群，架構轉變為精簡、窄焦點的 agent 微服務，任務時間從小時級降至分鐘級。提出未來假說：檔案系統適配器可解決 context bloat，為大規模 agent 編排提供參考。

### 重點
- 架構演進：全能型 prompts → 專門化 agent 微服務（task time: 小時 → 分鐘）
- 窄焦點設計降低 context 負擔，提升執行效率
- 未來方向：檔案系統適配器解決 context bloat，提升可擴展性

**原文：** [infoq-ai-ml](https://www.infoq.com/presentations/multi-agent-system-lessons/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Presentation: What I Learned Building Multi-Agent Systems From Scratch

Paulo Arruda discusses Shopify’s evolution in AI adoption, moving from simple chat tools to a sophisticated swarm of specialized agents. He explains the transition from massive "all-in-one" prompts to lean, narrow-focused agent microservices that slash task times from hours to minutes. He also shares a future-looking hypothesis on using filesystem-based adapters to solve context bloat. By Paulo Arruda

</details>