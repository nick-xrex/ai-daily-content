---
id: inbox_9742ddca
date: 2026-06-03
source_ref: "[[00-inbox/.../inbox_9742ddca]]"
title: "Tool Calling vs MCP vs Skills: Why Modern AI Systems Ended Up Needing All Three"
url: https://mihirdave95.medium.com/tool-calling-vs-mcp-vs-skills-why-modern-ai-systems-ended-up-needing-all-three-4de8d021810a?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-03T12:36:00+00:00
fetched_at: 2026-06-04T00:57:16.300112+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文澄清工具調用、MCP、技能三者不是競爭關係而是互補層級。工具調用（Tool Calling）使模型決策執行外部操作，但規模化時直接暴露眾多工具導致提示膨脹、token 成本增加、工具選擇歧義。技能（Skills）將專業知識與工作流打包為可重用能力——「工具是動作，技能是能力」，例如 ProductionIncidentAnalysis 技能內含方法論與檢查清單，而非個別工具步驟。MCP（Model Context Protocol）是開放標準，統一連接 AI 應用與外部服務（GitHub、Jira、Slack），標準化工具來源而無改變模型調用方式。推薦架構：技能捕捉組織工作流，工具執行動作，MCP 提供標準化外部訪問。"
key_points:
  - "工具調用在規模化時的成本代價：更大提示、更高 token 使用、歧義工具選擇"
  - "技能vs工具：技能是能力（ProductionIncidentAnalysis 包含完整方法論），工具是單一動作"
  - "MCP 補充而非替代工具調用——統一接觸平台而保持模型調用機制不變"
tags: [mcp, tool-calling, skills, ai-architecture]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Tool Calling vs MCP vs Skills: Why Modern AI Systems Ended Up Needing All Three

本文澄清工具調用、MCP、技能三者不是競爭關係而是互補層級。工具調用（Tool Calling）使模型決策執行外部操作，但規模化時直接暴露眾多工具導致提示膨脹、token 成本增加、工具選擇歧義。技能（Skills）將專業知識與工作流打包為可重用能力——「工具是動作，技能是能力」，例如 ProductionIncidentAnalysis 技能內含方法論與檢查清單，而非個別工具步驟。MCP（Model Context Protocol）是開放標準，統一連接 AI 應用與外部服務（GitHub、Jira、Slack），標準化工具來源而無改變模型調用方式。推薦架構：技能捕捉組織工作流，工具執行動作，MCP 提供標準化外部訪問。

### 重點
- 工具調用在規模化時的成本代價：更大提示、更高 token 使用、歧義工具選擇
- 技能vs工具：技能是能力（ProductionIncidentAnalysis 包含完整方法論），工具是單一動作
- MCP 補充而非替代工具調用——統一接觸平台而保持模型調用機制不變

**原文：** [medium-tag-llm](https://mihirdave95.medium.com/tool-calling-vs-mcp-vs-skills-why-modern-ai-systems-ended-up-needing-all-three-4de8d021810a?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Mihir Dave"
published_at: 2026-06-03T12:36:00+00:00
fetched_at: 2026-06-03T18:14:01.059927+00:00
content_hash: "69dfa3dab996e60d8f96e27aa22dbdf23bdb934c9b69d07ccd05ce6ae05b4959"
lang: en
caption_quality: None
raw: true
topics: []
---

# Tool Calling vs MCP vs Skills: Why Modern AI Systems Ended Up Needing All Three

A few months ago, I was building an AI assistant for an internal application. Continue reading on Medium »

</details>