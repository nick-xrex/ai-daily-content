---
id: inbox_41bfa639
date: 2026-06-19
source_ref: "[[00-inbox/2026-06-19/2200-infoq-architecture-azure-functions-ships-serverless-agents-a934]]"
title: "Azure Functions Ships Serverless Agents Runtime at Build 2026"
url: https://www.infoq.com/news/2026/06/azure-functions-serverless-agent/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-19T08:57:00+00:00
fetched_at: 2026-06-19T22:14:33.383072+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Microsoft 在 Build 2026 大會宣布 Azure Functions 推出無伺服器代理執行時(public preview)。代理通過 .agent.md Markdown 檔案定義，支持 YAML 觸發器、1,400+ 內置連接器和沙箱執行環境。Azure Functions 團隊確認執行時不增加冷啟動開銷，也不收取標準 Flex Consumption 計費模式之外的額外溢價，使企業可更低成本地部署自主代理。"
key_points:
  - "Azure Functions 無伺服器代理執行時進入公開預覽，支持 .agent.md Markdown + YAML 觸發器定義"
  - "1,400+ 內置 MCP 連接器與沙箱執行，無冷啟動額外開銷"
  - "Flex Consumption 計費無額外溢價，降低代理部署成本門檻"
tags: [azure-functions, serverless-agents, mcp-connectors, agent-runtime, build-2026]
topics: [agents.mcp]
importance: 5
novelty: 5
insight_quality: 3
insight_type: announcement
deep_dive_candidate: true
deep_dive_approved: false
---

## Azure Functions Ships Serverless Agents Runtime at Build 2026

Microsoft 在 Build 2026 大會宣布 Azure Functions 推出無伺服器代理執行時(public preview)。代理通過 .agent.md Markdown 檔案定義，支持 YAML 觸發器、1,400+ 內置連接器和沙箱執行環境。Azure Functions 團隊確認執行時不增加冷啟動開銷，也不收取標準 Flex Consumption 計費模式之外的額外溢價，使企業可更低成本地部署自主代理。

### 重點
- Azure Functions 無伺服器代理執行時進入公開預覽，支持 .agent.md Markdown + YAML 觸發器定義
- 1,400+ 內置 MCP 連接器與沙箱執行，無冷啟動額外開銷
- Flex Consumption 計費無額外溢價，降低代理部署成本門檻

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/06/azure-functions-serverless-agent/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Azure Functions shipped a serverless agents runtime in public preview at Build 2026. Agents are defined in .agent.md markdown files with YAML triggers, MCP server access, 1,400+ connectors, and sandboxed execution. The Functions team confirmed to InfoQ that the runtime adds no cold start overhead and no billing premium beyond standard Flex Consumption. By Steef-Jan Wiggers

</details>