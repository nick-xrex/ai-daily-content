---
id: inbox_b427f46a
date: 2026-06-30
source_ref: "[[00-inbox/2026-06-30/2331-infoq-architecture-aws-launches-lambda-microvms-for-isolate-7e66]]"
title: "AWS Launches Lambda MicroVMs for Isolated Agent and User Code Execution"
url: https://www.infoq.com/news/2026/06/aws-lambda-microvms/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-30T09:09:00+00:00
fetched_at: 2026-07-02T00:25:35.387975+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 推出 Lambda MicroVMs，擴展無伺服器計算能力。每個使用者會話或 AI 代理運行在獨立的 Firecracker 虛擬機中，實現硬體級隔離。快照機制允許快速啟動，狀態可保留 8 小時，適合長運行代理。該服務針對隔離代理和使用者代碼執行場景設計。Reddit 社群分析顯示，最小設置成本約 $3.03/天，是 Fargate Spot 定價的 9 倍，成本與隔離度的權衡值得謹慎評估。"
key_points:
  - "Firecracker VM 硬體級隔離 + 快照式快速啟動 + 8 小時狀態保留，支援長運行代理"
  - "最小成本 $3.03/天，Fargate Spot 定價的 9 倍，成本權衡需仔細評估"
  - "新無伺服器原語針對 agent 隔離和使用者代碼執行場景，擴展 Lambda 生態"
tags: [aws-lambda, serverless-compute, firecracker-vm, agent-isolation, cost-analysis]
topics: []
importance: 5
novelty: 5
insight_quality: 4
insight_type: announcement
deep_dive_candidate: true
deep_dive_approved: false
---

## AWS Launches Lambda MicroVMs for Isolated Agent and User Code Execution

AWS 推出 Lambda MicroVMs，擴展無伺服器計算能力。每個使用者會話或 AI 代理運行在獨立的 Firecracker 虛擬機中，實現硬體級隔離。快照機制允許快速啟動，狀態可保留 8 小時，適合長運行代理。該服務針對隔離代理和使用者代碼執行場景設計。Reddit 社群分析顯示，最小設置成本約 $3.03/天，是 Fargate Spot 定價的 9 倍，成本與隔離度的權衡值得謹慎評估。

### 重點
- Firecracker VM 硬體級隔離 + 快照式快速啟動 + 8 小時狀態保留，支援長運行代理
- 最小成本 $3.03/天，Fargate Spot 定價的 9 倍，成本權衡需仔細評估
- 新無伺服器原語針對 agent 隔離和使用者代碼執行場景，擴展 Lambda 生態

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/06/aws-lambda-microvms/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AWS launched Lambda MicroVMs, a new serverless compute primitive that runs each user session or AI agent in its own Firecracker virtual machine with hardware-level isolation, snapshot-based rapid launch, and state preservation for up to eight hours. Reddit community analysis found the minimum setup costs $3.03/day, roughly 9x Fargate spot pricing. By Steef-Jan Wiggers

</details>