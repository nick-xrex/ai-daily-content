---
id: inbox_0ce46876
date: 2026-05-27
source_ref: "[[00-inbox/2026-05-27/2345-infoq-ai-ml-sarang-kulkarni-on-lessons-from-building-9124]]"
title: "Sarang Kulkarni on Lessons from Building Deep Research Agents in Production"
url: https://www.infoq.com/news/2026/05/kulkarni-deep-research-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-05-27T07:45:00+00:00
fetched_at: 2026-05-27T23:54:48.993807+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Sarang Kulkarni 在 Arc of AI Conference 2026 分享 Thoughtworks 在生产环境中部署深度研究代理系统的实战经验。Deep Research Agentic Systems 通过多步骤推理、多跳信息检索（multi-hop retrieval）和结构化报告生成，能自主完成复杂研究任务。演讲涵盖代理系统架构设计、生产部署的关键挑战（上下文管理、推理稳定性、成本控制）、以及从开发到运营的经验教训，为企业落地多代理研究系统提供参考。"
key_points:
  - "多步骤推理与多跳信息检索：代理逐步分解复杂问题，动态获取和综合跨源信息"
  - "结构化报告生成：从推理过程产出可机读、可审计的分析报告，便于决策验证"
  - "生产部署的关键经验：上下文窗口管理、代理决策可解释性、成本与延迟的权衡"
tags: [deep-research-agents, multi-step-reasoning, production-deployment, multi-hop-retrieval]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Sarang Kulkarni on Lessons from Building Deep Research Agents in Production

Sarang Kulkarni 在 Arc of AI Conference 2026 分享 Thoughtworks 在生产环境中部署深度研究代理系统的实战经验。Deep Research Agentic Systems 通过多步骤推理、多跳信息检索（multi-hop retrieval）和结构化报告生成，能自主完成复杂研究任务。演讲涵盖代理系统架构设计、生产部署的关键挑战（上下文管理、推理稳定性、成本控制）、以及从开发到运营的经验教训，为企业落地多代理研究系统提供参考。

### 重點
- 多步骤推理与多跳信息检索：代理逐步分解复杂问题，动态获取和综合跨源信息
- 结构化报告生成：从推理过程产出可机读、可审计的分析报告，便于决策验证
- 生产部署的关键经验：上下文窗口管理、代理决策可解释性、成本与延迟的权衡

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/05/kulkarni-deep-research-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Deep Research Agentic Systems are AI Agents designed to conduct multi-step research for complex tasks using dynamic reasoning, multi-hop information retrieval, and generate structured analytical reports. Sarang Kulkarni from Thoughtworks spoke at Arc of AI Conference 2026 on how to deploy multi-agent research systems for deep reasoning, and the lessons learned from developing Deep Research Agents. By Srini Penchikala

</details>