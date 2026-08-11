---
id: inbox_c5ed77d6
date: 2026-08-07
source_ref: "[[00-inbox/.../inbox_c5ed77d6]]"
title: "Instacart Builds Blueberry, an AI-Powered Assistant to Help On-Call Engineers Investigate Incidents"
url: https://www.infoq.com/news/2026/08/instacart-blueberry-sre-ai/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-08-07T14:34:00+00:00
fetched_at: 2026-08-11T01:20:53.146142+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Instacart 開發 Blueberry，一個 AI 輔助的事件響應系統，幫助 on-call 工程師更快診斷生產問題。系統結合 AI agents、運營數據和事件歷史知識，透過 Slack 生成有依據的根因假設。採用並行子代理和 MCP 整合架構，使 AI 分析與人工決策相協調，縮短調查時間同時保留工程師主控權。"
key_points:
  - "Blueberry 架構：並行子代理 + MCP 整合 + 事件歷史資料庫，在 Slack 即時協作"
  - "設計模式：AI 生成假設但保留人類最終決策，避免盲目自動化風險"
  - "多層融合：metrics、logs、code、incident history 的多模態資料整合"
tags: [instacart-blueberry, incident-response, mcp-integration, ai-agents, sre]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Instacart Builds Blueberry, an AI-Powered Assistant to Help On-Call Engineers Investigate Incidents

Instacart 開發 Blueberry，一個 AI 輔助的事件響應系統，幫助 on-call 工程師更快診斷生產問題。系統結合 AI agents、運營數據和事件歷史知識，透過 Slack 生成有依據的根因假設。採用並行子代理和 MCP 整合架構，使 AI 分析與人工決策相協調，縮短調查時間同時保留工程師主控權。

### 重點
- Blueberry 架構：並行子代理 + MCP 整合 + 事件歷史資料庫，在 Slack 即時協作
- 設計模式：AI 生成假設但保留人類最終決策，避免盲目自動化風險
- 多層融合：metrics、logs、code、incident history 的多模態資料整合

**原文：** [infoq-main](https://www.infoq.com/news/2026/08/instacart-blueberry-sre-ai/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Instacart Builds Blueberry, an AI-Powered Assistant to Help On-Call Engineers Investigate Incidents

Instacart introduced Blueberry, an AI-assisted incident response system that helps on-call engineers investigate production issues faster. It combines AI agents, operational data, and historical incident knowledge to generate grounded root cause hypotheses in Slack. It uses parallel subagents, MCP integrations, and incident history to reduce investigation time while keeping engineers in control. By Leela Kumili

</details>