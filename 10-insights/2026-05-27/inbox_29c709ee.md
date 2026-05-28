---
id: inbox_29c709ee
date: 2026-05-27
source_ref: "[[00-inbox/2026-05-27/2345-infoq-main-azure-logic-apps-adds-sandboxed-code-int-c7a0]]"
title: "Azure Logic Apps Adds Sandboxed Code Interpreters to Agent Workflows"
url: https://www.infoq.com/news/2026/05/azure-logic-apps-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-27T09:45:00+00:00
fetched_at: 2026-05-27T23:53:01.578811+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Microsoft 在 Azure Logic Apps 中新增沙盒化代碼執行器，支援在 Hyper-V 隔離環境執行 Python、JavaScript、C#、PowerShell 程式碼。Agent workflows 可動態生成並運行程式碼，架構師可按工作流程級別精細控制模型選擇。此舉將 Logic Apps 定位為 integration 領域的 agent 平台，與 Copilot Studio 和 Foundry 競爭。

```mermaid
graph LR
    A[Agent Workflow] --> B{Code Generation}
    B --> C[Python/JS/C#/PowerShell]
    C --> D[Hyper-V Isolated Execution]
    D --> E[Result Return]
    F[Model Selection<br/>Per Workflow] -.->|controls| A
    style D fill:#90EE90
```"
key_points:
  - "Hyper-V 隔離環境執行多語言程式碼（Python/JS/C#/PowerShell），隔離安全風險"
  - "Agent workflows 內置代碼生成與執行，消除外部工具依賴，加快集成速度"
  - "工作流級模型選擇控制，使 Logic Apps 從集成工具進化為 agentic 平台"
tags: [azure-logic-apps, agent-workflows, sandboxed-execution, integration]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Azure Logic Apps Adds Sandboxed Code Interpreters to Agent Workflows

Microsoft 在 Azure Logic Apps 中新增沙盒化代碼執行器，支援在 Hyper-V 隔離環境執行 Python、JavaScript、C#、PowerShell 程式碼。Agent workflows 可動態生成並運行程式碼，架構師可按工作流程級別精細控制模型選擇。此舉將 Logic Apps 定位為 integration 領域的 agent 平台，與 Copilot Studio 和 Foundry 競爭。

```mermaid
graph LR
    A[Agent Workflow] --> B{Code Generation}
    B --> C[Python/JS/C#/PowerShell]
    C --> D[Hyper-V Isolated Execution]
    D --> E[Result Return]
    F[Model Selection<br/>Per Workflow] -.->|controls| A
    style D fill:#90EE90
```

### 重點
- Hyper-V 隔離環境執行多語言程式碼（Python/JS/C#/PowerShell），隔離安全風險
- Agent workflows 內置代碼生成與執行，消除外部工具依賴，加快集成速度
- 工作流級模型選擇控制，使 Logic Apps 從集成工具進化為 agentic 平台

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/azure-logic-apps-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Microsoft added sandboxed code interpreters to Azure Logic Apps, enabling agents within integration workflows to generate and execute Python, JavaScript, C#, and PowerShell in Hyper-V isolated sessions. Architects get full control over model selection per workflow. The capability positions Logic Apps as an agent platform for integration alongside Foundry and Copilot Studio. By Steef-Jan Wiggers

</details>