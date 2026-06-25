---
id: inbox_40a2a64b
date: 2026-06-25
source_ref: "[[00-inbox/2026-06-25/2200-infoq-architecture-grab-builds-secure-agentic-ai-workload-p-17f1]]"
title: "Grab Builds Secure Agentic AI Workload Platform"
url: https://www.infoq.com/news/2026/06/grab-ai-platform/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-25T02:08:00+00:00
fetched_at: 2026-06-25T22:14:46.434489+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Grab 安全團隊推出 Palana，一個 Kubernetes-native 的安全執行平台，專用於安全運行自主 AI agents。Palana 透過隔離命名空間、out-of-process 控制平面和 Vault-backed secrets 等基礎設施層級機制，從根本上解決模型驅動 agents 在 tool-use、code-writing 和 prompt injection 上的不可預測威脅——這些是傳統決定性軟體所沒有的新安全類別。"
key_points:
  - "Palana 使用隔離命名空間、out-of-process 控制平面和 Vault-backed secrets，在基礎設施層級防禦 agents"
  - "AI agents 的三大威脅：unpredictable tool-use、code-writing、prompt injection（相異於傳統決定性軟體）"
  - "Kubernetes-native 設計便於容器化部署和安全隔離"
tags: [agent-security, kubernetes, infrastructure-safety, grab]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Grab Builds Secure Agentic AI Workload Platform

Grab 安全團隊推出 Palana，一個 Kubernetes-native 的安全執行平台，專用於安全運行自主 AI agents。Palana 透過隔離命名空間、out-of-process 控制平面和 Vault-backed secrets 等基礎設施層級機制，從根本上解決模型驅動 agents 在 tool-use、code-writing 和 prompt injection 上的不可預測威脅——這些是傳統決定性軟體所沒有的新安全類別。

### 重點
- Palana 使用隔離命名空間、out-of-process 控制平面和 Vault-backed secrets，在基礎設施層級防禦 agents
- AI agents 的三大威脅：unpredictable tool-use、code-writing、prompt injection（相異於傳統決定性軟體）
- Kubernetes-native 設計便於容器化部署和安全隔離

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/06/grab-ai-platform/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Grab's security team built Palana, a Kubernetes-native secure execution platform, to run autonomous AI agents safely. Unlike deterministic software, model-driven agents exhibit unpredictable tool-use, code-writing, and prompt injection risks. Palana contains these threats at the infrastructure level using isolated namespaces, out-of-process control planes, and proxy-mediated, Vault-backed secrets. By Patrick Farry

</details>