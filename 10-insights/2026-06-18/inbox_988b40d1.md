---
id: inbox_988b40d1
date: 2026-06-18
source_ref: "[[00-inbox/2026-06-18/2200-medium-tag-llm-fleet-engineering-c195]]"
title: "Fleet Engineering"
url: https://cobusgreyling.medium.com/fleet-engineering-67a0f25991c1?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-18T12:38:08+00:00
fetched_at: 2026-06-18T22:14:42.173824+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LangSmith Fleet 定義並解決「多智能體治理」問題：企業不再只有一個智能體，而是數十個跨部門部署的智能體。核心挑戰從「我們能否構建智能體？」轉向「誰擁有、如何治理、怎樣稽核」。Fleet 建立四大支柱：(1) 代理—知識工作者用自然語言敘述任務；(2) 改進—從真實使用與反饋學習；(3) 批准—敏感操作需人工批准；(4) 連接—OAuth 與 MCP 伺服器管理工具存取。可觀測性為基礎，系統區分 Claws（固定憑證）和 Assistants（用戶級 OAuth）。"
key_points:
  - "企業智能體數量從「1～2 個」快速擴展至「數十個」，治理從工程問題轉向組織問題"
  - "LangSmith Fleet 四大支柱：自然語言代理、使用反饋驅動改進、敏感操作人工批准、OAuth+MCP 權限管理"
  - "可觀測性（每個動作都可追蹤）是基礎；區分 Claws（固定身份）與 Assistants（用戶身份）的身份管理方案經常被低估"
tags: [fleet-engineering, multi-agent-governance, langsmith, agent-orchestration, observability]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Fleet Engineering

LangSmith Fleet 定義並解決「多智能體治理」問題：企業不再只有一個智能體，而是數十個跨部門部署的智能體。核心挑戰從「我們能否構建智能體？」轉向「誰擁有、如何治理、怎樣稽核」。Fleet 建立四大支柱：(1) 代理—知識工作者用自然語言敘述任務；(2) 改進—從真實使用與反饋學習；(3) 批准—敏感操作需人工批准；(4) 連接—OAuth 與 MCP 伺服器管理工具存取。可觀測性為基礎，系統區分 Claws（固定憑證）和 Assistants（用戶級 OAuth）。

### 重點
- 企業智能體數量從「1～2 個」快速擴展至「數十個」，治理從工程問題轉向組織問題
- LangSmith Fleet 四大支柱：自然語言代理、使用反饋驅動改進、敏感操作人工批准、OAuth+MCP 權限管理
- 可觀測性（每個動作都可追蹤）是基礎；區分 Claws（固定身份）與 Assistants（用戶身份）的身份管理方案經常被低估

**原文：** [medium-tag-llm](https://cobusgreyling.medium.com/fleet-engineering-67a0f25991c1?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

LangSmith Fleet names the problem every enterprise is about to have&#x2026;not one agent, but a fleet of agents&#x2026; Continue reading on Medium »

</details>