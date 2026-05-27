---
id: inbox_a873983c
date: 2026-05-26
source_ref: "[[00-inbox/2026-05-26/0023-medium-towards-data-science-what-is-a-data-agent-5f65]]"
title: "What Is a Data Agent?"
url: https://towardsdatascience.com/what-is-a-data-agent/
source: medium-towards-data-science
published_at: 2026-05-26T16:30:00+00:00
fetched_at: 2026-05-27T00:31:50.799275+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "資料代理（Data Agent）定義為「可對話的報表」，特別在 Microsoft Fabric 實現上：使用者用自然語言提問，代理自動選擇資料源、生成對應查詢（SQL/DAX/KQL）、驗證並執行，返回結果而非靜態視覺化。此方法改變分析師工作流——從手動構建儀表板轉為定義資料代理邏輯，同時讓業務使用者在熟悉的 AI 工具（如 M365 Copilot）內直接存取insights，降低 BI 工具學習障礙，實現自助分析。"
key_points:
  - "資料代理核心機制：自然語言查詢 → 源選擇 → 查詢生成 → 驗證 → 執行，返回結果表格而非儀表板"
  - "分析師工作轉變：從儀表板設計改為資料模型邏輯與代理指令設計，減少重複可視化工作"
  - "自助分析民主化：業務使用者在日常工具（M365 Copilot 等）內存取insights，無需學習 BI 平台或切換應用"
tags: [data-agent, microsoft-fabric, natural-language-query, analytics-automation, self-service-analytics]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## What Is a Data Agent?

資料代理（Data Agent）定義為「可對話的報表」，特別在 Microsoft Fabric 實現上：使用者用自然語言提問，代理自動選擇資料源、生成對應查詢（SQL/DAX/KQL）、驗證並執行，返回結果而非靜態視覺化。此方法改變分析師工作流——從手動構建儀表板轉為定義資料代理邏輯，同時讓業務使用者在熟悉的 AI 工具（如 M365 Copilot）內直接存取insights，降低 BI 工具學習障礙，實現自助分析。

### 重點
- 資料代理核心機制：自然語言查詢 → 源選擇 → 查詢生成 → 驗證 → 執行，返回結果表格而非儀表板
- 分析師工作轉變：從儀表板設計改為資料模型邏輯與代理指令設計，減少重複可視化工作
- 自助分析民主化：業務使用者在日常工具（M365 Copilot 等）內存取insights，無需學習 BI 平台或切換應用

**原文：** [medium-towards-data-science](https://towardsdatascience.com/what-is-a-data-agent/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A simple explanation of what a data agent is and how it works 
 The post What Is a Data Agent? appeared first on Towards Data Science .

</details>