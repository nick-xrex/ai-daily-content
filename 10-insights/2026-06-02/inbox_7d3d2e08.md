---
id: inbox_7d3d2e08
date: 2026-06-02
source_ref: "[[00-inbox/2026-06-02/0030-medium-tag-claude-documenting-sql-server-databases-automat-d93e]]"
title: "Documenting SQL Server Databases Automatically with System Catalog Claude Skill"
url: https://medium.com/@lorenzouriel/documenting-sql-server-databases-automatically-with-system-catalog-claude-skill-22583c6c4f1b?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-06-02T20:01:01+00:00
fetched_at: 2026-06-03T00:44:37.334764+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "自動化 SQL Server 資料庫文件生成 Claude Skill。作者指出 SQL Server 的系統目錄檢視（sys.tables、sys.columns、sys.foreign_keys）已包含完整的結構化文件，只是需要提取和重新格式化。Skill 執行 8 個 SQL 查詢提取中繼資料（表結構、行數、外鍵關係等），轉換為可讀的 Markdown 文件並自動生成 ER 圖。無需額外的文件工具，直接利用 SQL Server 內建的組織結構。"
key_points:
  - "SQL Server 系統目錄已內建完整中繼資料，無需第三方文件工具"
  - "一個 Claude Skill + 8 個查詢就可自動生成 Markdown + ER 圖表"
  - "適用於自動化資料庫文件化工作流，降低手動維護成本"
tags: [sql-server, documentation-automation, claude-skill, metadata-extraction]
topics: [agents.mcp]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Documenting SQL Server Databases Automatically with System Catalog Claude Skill

自動化 SQL Server 資料庫文件生成 Claude Skill。作者指出 SQL Server 的系統目錄檢視（sys.tables、sys.columns、sys.foreign_keys）已包含完整的結構化文件，只是需要提取和重新格式化。Skill 執行 8 個 SQL 查詢提取中繼資料（表結構、行數、外鍵關係等），轉換為可讀的 Markdown 文件並自動生成 ER 圖。無需額外的文件工具，直接利用 SQL Server 內建的組織結構。

### 重點
- SQL Server 系統目錄已內建完整中繼資料，無需第三方文件工具
- 一個 Claude Skill + 8 個查詢就可自動生成 Markdown + ER 圖表
- 適用於自動化資料庫文件化工作流，降低手動維護成本

**原文：** [medium-tag-claude](https://medium.com/@lorenzouriel/documenting-sql-server-databases-automatically-with-system-catalog-claude-skill-22583c6c4f1b?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Not a Medium member? Read here! Continue reading on Medium »

</details>