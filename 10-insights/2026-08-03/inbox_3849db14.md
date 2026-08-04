---
id: inbox_3849db14
date: 2026-08-03
source_ref: "[[00-inbox/.../inbox_3849db14]]"
title: "Presentation: Architecting AI Systems for the Messy Reality of Enterprises: Why Agentic Compute is the Missing Layer"
url: https://www.infoq.com/presentations/agentic-compute/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-08-03T08:08:00+00:00
fetched_at: 2026-08-04T01:58:03.068023+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Arun Joseph 分析企業級代理平台架構，以 Deutsche Telekom 的 LMOS 為實例。核心洞見是「Agentic Compute」是被忽視的企業 AI 層次——簡單聊天機器人無法適應複雜的組織現實。企業需通過三個層面打破工具散亂和組織孤島：(1)核心平台抽象替代點對點工具集成，(2)短生命週期代理(ephemeral agents)實現動態工作流，(3)採用代理定義語言(ADL)標準化代理行為描述。這樣的架構允許企業從對話界面升級到真正的操作智能系統，跨越組織邊界自動協調任務。"
key_points:
  - "Agentic Compute 層需平台級抽象而非簡單 SDK：統一工具、記憶體、審計、權限管理"
  - "短生命週期代理(ephemeral agents)相比長駐程序更適合企業 workflow，降低狀態複雜性"
  - "Agent Definition Language(ADL)標準化和重用代理行為，類似基礎設施即代碼(IaC)的思路"
tags: [agentic-compute, agent-definition-language, enterprise-ai, operational-intelligence, lmos]
topics: [agents.mcp]
importance: 5
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Presentation: Architecting AI Systems for the Messy Reality of Enterprises: Why Agentic Compute is the Missing Layer

Arun Joseph 分析企業級代理平台架構，以 Deutsche Telekom 的 LMOS 為實例。核心洞見是「Agentic Compute」是被忽視的企業 AI 層次——簡單聊天機器人無法適應複雜的組織現實。企業需通過三個層面打破工具散亂和組織孤島：(1)核心平台抽象替代點對點工具集成，(2)短生命週期代理(ephemeral agents)實現動態工作流，(3)採用代理定義語言(ADL)標準化代理行為描述。這樣的架構允許企業從對話界面升級到真正的操作智能系統，跨越組織邊界自動協調任務。

### 重點
- Agentic Compute 層需平台級抽象而非簡單 SDK：統一工具、記憶體、審計、權限管理
- 短生命週期代理(ephemeral agents)相比長駐程序更適合企業 workflow，降低狀態複雜性
- Agent Definition Language(ADL)標準化和重用代理行為，類似基礎設施即代碼(IaC)的思路

**原文：** [infoq-main](https://www.infoq.com/presentations/agentic-compute/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Presentation: Architecting AI Systems for the Messy Reality of Enterprises: Why Agentic Compute is the Missing Layer

Arun Joseph shares real-world insights on scaling enterprise agentic platforms like Deutsche Telekom’s LMOS. He discusses bridging organizational fault lines, replacing tool sprawl with core platform abstractions, and moving beyond basic chatbots to operational intelligence systems through ephemeral agents and an Agent Definition Language (ADL). By Arun Joseph

</details>