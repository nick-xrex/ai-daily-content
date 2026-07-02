---
id: inbox_e31e1abe
date: 2026-06-30
source_ref: "[[00-inbox/2026-06-30/2331-infoq-main-aws-launches-lambda-microvms-for-isolate-bcff]]"
title: "AWS Launches Lambda MicroVMs for Isolated Agent and User Code Execution"
url: https://www.infoq.com/news/2026/06/aws-lambda-microvms/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-30T09:09:00+00:00
fetched_at: 2026-07-02T00:21:41.697388+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 推出 Lambda MicroVMs，一種新無伺服器計算原始型態，為每個用戶會話或 AI 代理在獨立 Firecracker 虛擬機中執行，提供硬體隔離、秒級快照啟動、八小時狀態保留等能力。社群成本分析顯示最低月費約 $3.03/天，約為 Fargate Spot 價格的 9 倍，代表新的隔離和成本權衡模式。"
key_points:
  - "硬體隔離代理沙盒：Firecracker VM 提供內核級隔離，每代理獨立虛擬機，安全邊界明確"
  - "快照啟動 + 八小時狀態持化：秒級啟動、跨會話狀態保留，適合有狀態代理和長執行工作負載"
  - "成本模型突變：$3.03/天基礎費用 ≈ 9× Fargate Spot，適合高隔離需求的低量任務，不適用高吞吐量通用無伺服器"
tags: [aws-lambda, microvms, firecracker, agent-execution, serverless-compute]
topics: []
importance: 5
novelty: 5
insight_quality: 4
insight_type: announcement
deep_dive_candidate: true
deep_dive_approved: false
---

## AWS Launches Lambda MicroVMs for Isolated Agent and User Code Execution

AWS 推出 Lambda MicroVMs，一種新無伺服器計算原始型態，為每個用戶會話或 AI 代理在獨立 Firecracker 虛擬機中執行，提供硬體隔離、秒級快照啟動、八小時狀態保留等能力。社群成本分析顯示最低月費約 $3.03/天，約為 Fargate Spot 價格的 9 倍，代表新的隔離和成本權衡模式。

### 重點
- 硬體隔離代理沙盒：Firecracker VM 提供內核級隔離，每代理獨立虛擬機，安全邊界明確
- 快照啟動 + 八小時狀態持化：秒級啟動、跨會話狀態保留，適合有狀態代理和長執行工作負載
- 成本模型突變：$3.03/天基礎費用 ≈ 9× Fargate Spot，適合高隔離需求的低量任務，不適用高吞吐量通用無伺服器

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/aws-lambda-microvms/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AWS launched Lambda MicroVMs, a new serverless compute primitive that runs each user session or AI agent in its own Firecracker virtual machine with hardware-level isolation, snapshot-based rapid launch, and state preservation for up to eight hours. Reddit community analysis found the minimum setup costs $3.03/day, roughly 9x Fargate spot pricing. By Steef-Jan Wiggers

</details>