---
id: inbox_c12745b0
date: 2026-06-25
source_ref: "[[00-inbox/2026-06-25/2200-infoq-ai-ml-grab-builds-secure-agentic-ai-workload-p-45c9]]"
title: "Grab Builds Secure Agentic AI Workload Platform"
url: https://www.infoq.com/news/2026/06/grab-ai-platform/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-06-25T02:08:00+00:00
fetched_at: 2026-06-25T22:12:40.073179+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Grab 的安全團隊開發了 Palana，一個專為安全運行自主 AI 代理而設計的 Kubernetes 原生平台。與確定性軟體不同，模型驅動的代理具有不可預測的工具使用、代碼生成和提示注入風險。Palana 通過基礎設施級的隔離機制（包括隔離命名空間、進程外控制平面、以及 Vault 支持的代理式秘密管理）來遏制這些威脅。這種方法表明，AI 代理的安全管控應該在基礎設施層面實現，而非僅依賴應用層防護。"
key_points:
  - "Palana 使用隔離命名空間 + 進程外控制平面 + Vault 秘密代理實現代理級安全隔離"
  - "針對模型驅動代理的不可預測工具使用、代碼生成和提示注入風險"
  - "基礎設施級安全防護相比應用層防護更有效"
tags: [agent-security, kubernetes, zero-trust]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Grab Builds Secure Agentic AI Workload Platform

Grab 的安全團隊開發了 Palana，一個專為安全運行自主 AI 代理而設計的 Kubernetes 原生平台。與確定性軟體不同，模型驅動的代理具有不可預測的工具使用、代碼生成和提示注入風險。Palana 通過基礎設施級的隔離機制（包括隔離命名空間、進程外控制平面、以及 Vault 支持的代理式秘密管理）來遏制這些威脅。這種方法表明，AI 代理的安全管控應該在基礎設施層面實現，而非僅依賴應用層防護。

### 重點
- Palana 使用隔離命名空間 + 進程外控制平面 + Vault 秘密代理實現代理級安全隔離
- 針對模型驅動代理的不可預測工具使用、代碼生成和提示注入風險
- 基礎設施級安全防護相比應用層防護更有效

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/06/grab-ai-platform/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Grab's security team built Palana, a Kubernetes-native secure execution platform, to run autonomous AI agents safely. Unlike deterministic software, model-driven agents exhibit unpredictable tool-use, code-writing, and prompt injection risks. Palana contains these threats at the infrastructure level using isolated namespaces, out-of-process control planes, and proxy-mediated, Vault-backed secrets. By Patrick Farry

</details>