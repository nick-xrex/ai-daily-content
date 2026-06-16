---
id: inbox_d9bb05e4
date: 2026-06-15
source_ref: "[[00-inbox/2026-06-15/2348-simon-willison-datasette-agent-0-3a0-78b0]]"
title: "datasette-agent 0.3a0"
url: https://simonwillison.net/2026/Jun/15/datasette-agent/#atom-everything
source: simon-willison
published_at: 2026-06-15T17:19:27+00:00
fetched_at: 2026-06-15T23:53:14.488540+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-agent 0.3a0 alpha 版本發布，新增 execute_write_sql 工具允許 agent 在請求使用者批准後安全寫入資料庫並尊重使用者權限（#27）。chat 終端模式獲得增強支援批准機制，新增 --root、--yes 和 --unsafe 三個選項（#30），並支援純文本替代方案便於 CLI 顯示（#31）。使用者現可透過自然語言提示直接修改資料庫，如「建立記錄表」或「新增關於 X 的註記」，實現人工智慧與資料庫安全修改的深度整合。"
key_points:
  - "新工具 execute_write_sql（#27）支援使用者批准機制後安全寫入資料庫並遵守權限限制"
  - "chat 終端新增 --root、--yes、--unsafe 選項（#30），支援自動批准和根權限執行"
  - "純文本替代方案（#31）讓 CLI 模式無需 HTML 亦能顯示工具輸出"
tags: [datasette-agent, execute-write-sql, database-modification, tool-use, approval-flow]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-agent 0.3a0

datasette-agent 0.3a0 alpha 版本發布，新增 execute_write_sql 工具允許 agent 在請求使用者批准後安全寫入資料庫並尊重使用者權限（#27）。chat 終端模式獲得增強支援批准機制，新增 --root、--yes 和 --unsafe 三個選項（#30），並支援純文本替代方案便於 CLI 顯示（#31）。使用者現可透過自然語言提示直接修改資料庫，如「建立記錄表」或「新增關於 X 的註記」，實現人工智慧與資料庫安全修改的深度整合。

### 重點
- 新工具 execute_write_sql（#27）支援使用者批准機制後安全寫入資料庫並遵守權限限制
- chat 終端新增 --root、--yes、--unsafe 選項（#30），支援自動批准和根權限執行
- 純文本替代方案（#31）讓 CLI 模式無需 HTML 亦能顯示工具輸出

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/15/datasette-agent/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-agent 0.3a0 
 
 
 New tool, execute_write_sql , which requests user approval and then writes to a database - taking user permissions into account. #27 
 
 
 I added a mechanism for asking user approval in datasette agent 0.2a0 . The new execute_write_sql tool can now prompt the user for all kinds of useful operations. Here's an example where I add some pelican sightings to my pelican_sightings table: 
 
 The new version also enhances the datasette agent chat terminal mode to support approvals, and adds several new options including --unsafe mode for auto-approving them: 
 
 
 datasette agent chat can execute tools that require user approval. #30 
 Three new options for datasette agent chat - --root to run as root, --yes to approve all ask user questions, and --unsafe for both. 
 Tools can now provide plain text alternatives to HTML, for display in the datasette agent chat CLI. #31 
 
 
 The datasette agent chat content.db -m gpt-5.5 --unsafe command can now be used to chat directly with a specific database and directly modify it through prompts like "create a notes table", "add a note about X" etc. 
 
 
 Tags: projects , ai , datasette , annotated-release-notes , generative-ai , llms , llm-tool-use , datasette-agent

</details>