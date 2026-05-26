---
id: inbox_c2a21aab
date: 2026-05-25
source_ref: "[[00-inbox/2026-05-25/0015-medium-towards-data-science-introducing-the-agent-toolkit-for-amazon-c519]]"
title: "Introducing the Agent Toolkit for Amazon Web Services"
url: https://towardsdatascience.com/introducing-the-agent-toolkit-for-amazon-web-services/
source: medium-towards-data-science
published_at: 2026-05-25T12:00:00+00:00
fetched_at: 2026-05-26T00:30:12.820839+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 發布開源 Agent Toolkit，涵蓋 15,000+ AWS API 調用，分為三大外掛：aws-core（通用開發）、aws-agents（Bedrock 代理工作流）、aws-data-analytics（S3 Tables、Glue、Athena、向量儲存）。工具透過 MCP 伺服器實現，提供策劃任務特定指令、即時文檔存取、沙盒指令碼執行和 IAM 身份驗證控制，相容 Claude Code、Cursor、Codex、Kiro、VS Code、Windsurf 等多種編碼代理。實例展示 32 分鐘內自動供應完整棧：VPC、安全群組、RDS 資料庫、IAM 角色、Glue ETL 作業和 Athena 目錄，透過 CloudWatch/CloudTrail 審計。"
key_points:
  - "AWS Agent Toolkit 開源，15,000+ API 調用覆蓋，三外掛架構 + MCP 伺服器實現 IAM 上下文條件金鑰和多 IDE 相容"
  - "端到端自動化示例：32 分鐘內完成 VPC+RDS+Glue+Athena 供應，展示代理自主基礎設施決策（檢查既有資源、避免服務特定陷阱）"
  - "關鍵特性：即時 AWS 文檔存取、沙盒指令碼執行、CloudWatch/CloudTrail 原生審計，支援 Claude Code/Cursor/Codex/Kiro/VS Code/Windsurf"
tags: [aws-toolkit, agent-toolkit, mcp-server, infrastructure-automation, multi-ide]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: announcement
deep_dive_candidate: true
deep_dive_approved: false
---

## Introducing the Agent Toolkit for Amazon Web Services

AWS 發布開源 Agent Toolkit，涵蓋 15,000+ AWS API 調用，分為三大外掛：aws-core（通用開發）、aws-agents（Bedrock 代理工作流）、aws-data-analytics（S3 Tables、Glue、Athena、向量儲存）。工具透過 MCP 伺服器實現，提供策劃任務特定指令、即時文檔存取、沙盒指令碼執行和 IAM 身份驗證控制，相容 Claude Code、Cursor、Codex、Kiro、VS Code、Windsurf 等多種編碼代理。實例展示 32 分鐘內自動供應完整棧：VPC、安全群組、RDS 資料庫、IAM 角色、Glue ETL 作業和 Athena 目錄，透過 CloudWatch/CloudTrail 審計。

### 重點
- AWS Agent Toolkit 開源，15,000+ API 調用覆蓋，三外掛架構 + MCP 伺服器實現 IAM 上下文條件金鑰和多 IDE 相容
- 端到端自動化示例：32 分鐘內完成 VPC+RDS+Glue+Athena 供應，展示代理自主基礎設施決策（檢查既有資源、避免服務特定陷阱）
- 關鍵特性：即時 AWS 文檔存取、沙盒指令碼執行、CloudWatch/CloudTrail 原生審計，支援 Claude Code/Cursor/Codex/Kiro/VS Code/Windsurf

**原文：** [medium-towards-data-science](https://towardsdatascience.com/introducing-the-agent-toolkit-for-amazon-web-services/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

It’s like having your own personal expert AWS solutions architect and data engineer rolled into one. 
 The post Introducing the Agent Toolkit for Amazon Web Services appeared first on Towards Data Science .

</details>