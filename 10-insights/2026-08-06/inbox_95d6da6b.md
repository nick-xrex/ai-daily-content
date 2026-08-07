---
id: inbox_95d6da6b
date: 2026-08-06
source_ref: "[[00-inbox/.../inbox_95d6da6b]]"
title: "Pods as Workers, Not Agents: Rethinking the Deployment Unit for AI Agents on Kubernetes"
url: https://www.infoq.com/news/2026/08/pod-deployment-unit-ai-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-08-06T06:00:00+00:00
fetched_at: 2026-08-07T01:28:50.284765+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Kubernetes 部署 AI agents 的关键问题是是否应该一个 Pod 对应一个 agent。kagent 项目主张不应该——因为 agents 具有突发性、生命周期短、可生成子 agents、需等待人工审批的特性，一 Pod 一 agent 的模式过度浪费资源。Agent-substrate 通过引入控制平面，将逻辑 \"Actors\" 调度到长期运行的 worker Pods 上，实现更有效的资源利用和成本优化。这一设计模式改变了对 Kubernetes 上 agents 部署单元的传统认知。"
key_points:
  - "Agents 的短生命周期和突发性特征决定了不适合一 Pod 一 agent 的传统部署模式"
  - "Agent-substrate 控制平面将逻辑 agents 与物理 worker Pods 解耦，支持多个 agents 共享基础设施"
  - "多 agents 共享 worker Pods 模式显著降低资源浪费和运营成本"
tags: [kubernetes, ai-agents, deployment-patterns, resource-optimization, container-orchestration]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Pods as Workers, Not Agents: Rethinking the Deployment Unit for AI Agents on Kubernetes

Kubernetes 部署 AI agents 的关键问题是是否应该一个 Pod 对应一个 agent。kagent 项目主张不应该——因为 agents 具有突发性、生命周期短、可生成子 agents、需等待人工审批的特性，一 Pod 一 agent 的模式过度浪费资源。Agent-substrate 通过引入控制平面，将逻辑 "Actors" 调度到长期运行的 worker Pods 上，实现更有效的资源利用和成本优化。这一设计模式改变了对 Kubernetes 上 agents 部署单元的传统认知。

### 重點
- Agents 的短生命周期和突发性特征决定了不适合一 Pod 一 agent 的传统部署模式
- Agent-substrate 控制平面将逻辑 agents 与物理 worker Pods 解耦，支持多个 agents 共享基础设施
- 多 agents 共享 worker Pods 模式显著降低资源浪费和运营成本

**原文：** [infoq-main](https://www.infoq.com/news/2026/08/pod-deployment-unit-ai-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Pods as Workers, Not Agents: Rethinking the Deployment Unit for AI Agents on Kubernetes

Running AI agents on Kubernetes raises a key question: should each agent get its own Pod? The kagent project argues no—agents are bursty, short-lived, can spawn subagents, and may wait for human approval, making one Pod per agent wasteful. Agent-substrate adds a control plane to schedule logical “Actors” onto long-lived worker Pods. By Mark Silvester

</details>