---
id: inbox_27a9940e
date: 2026-06-12
source_ref: "[[00-inbox/2026-06-12/0336-medium-tag-claude-the-ai-loops-fight-isnt-about-ai-loops-0377]]"
title: "The ‘AI loops’ fight isn’t about AI loops"
url: https://medium.com/@meghanaharishankara/the-ai-loops-fight-isn-t-about-ai-loops-f87fe6d7e454?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-06-12T23:20:45+00:00
fetched_at: 2026-06-13T03:52:24.113889+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者駁斥關於「AI 迴圈」(AI loops) 的爭論本質上是結構性討論，實則關鍵在於迴圈內容和工程本質的改變。迴圈概念並非新穎——ralph loop 模式源自 2025 年 7 月的簡單 bash while 迴圈，類同 Kubernetes 控制迴圈、溫度恆溫器、CI 管線等已存在數十年的系統。真正新穎之處在於：LLM 控制器在「數量級更大的決策空間」運作；多代理監督配合共享狀態和故障恢復成為新興模式；反饋設計比迴圈結構本身更重要。實踐工程應聚焦：(1) 控制器設計（LLM 決策內容）；(2) 反饋品質（如測試結果等確定性信號）；(3) 停止條件（防止成本失控）。Peter Steinberger 的 X 文章達 220 萬次檢視，Claude Code 的 `/ralph-loop` 插件 178k 安裝，Boris Cherny（Claude Code 建構者）2025 年 12 月底已貢獻 259 個完全由 Claude Code 生成的 PR。"
key_points:
  - "ralph loop 模式源自 2025/7，實際上是 bash while 迴圈，迴圈結構本身不新穎，但 LLM 控制器在決策空間量級上有質變"
  - "Peter Steinberger 文章 220 萬次檢視、Claude Code `/ralph-loop` 178k 安裝、Uber 每人每工具月度限制 $1,500 月支出後僅 4 月即燒完年度預算，證明規模落地挑戰"
  - "關鍵不在循環結構而在於控制器設計、反饋品質、停止條件——這三者決定 LLM 迴圈可靠性"
tags: [ai-loops, claude-code, multi-agent-systems, control-loops, engineering-practices]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The ‘AI loops’ fight isn’t about AI loops

作者駁斥關於「AI 迴圈」(AI loops) 的爭論本質上是結構性討論，實則關鍵在於迴圈內容和工程本質的改變。迴圈概念並非新穎——ralph loop 模式源自 2025 年 7 月的簡單 bash while 迴圈，類同 Kubernetes 控制迴圈、溫度恆溫器、CI 管線等已存在數十年的系統。真正新穎之處在於：LLM 控制器在「數量級更大的決策空間」運作；多代理監督配合共享狀態和故障恢復成為新興模式；反饋設計比迴圈結構本身更重要。實踐工程應聚焦：(1) 控制器設計（LLM 決策內容）；(2) 反饋品質（如測試結果等確定性信號）；(3) 停止條件（防止成本失控）。Peter Steinberger 的 X 文章達 220 萬次檢視，Claude Code 的 `/ralph-loop` 插件 178k 安裝，Boris Cherny（Claude Code 建構者）2025 年 12 月底已貢獻 259 個完全由 Claude Code 生成的 PR。

### 重點
- ralph loop 模式源自 2025/7，實際上是 bash while 迴圈，迴圈結構本身不新穎，但 LLM 控制器在決策空間量級上有質變
- Peter Steinberger 文章 220 萬次檢視、Claude Code `/ralph-loop` 178k 安裝、Uber 每人每工具月度限制 $1,500 月支出後僅 4 月即燒完年度預算，證明規模落地挑戰
- 關鍵不在循環結構而在於控制器設計、反饋品質、停止條件——這三者決定 LLM 迴圈可靠性

**原文：** [medium-tag-claude](https://medium.com/@meghanaharishankara/the-ai-loops-fight-isn-t-about-ai-loops-f87fe6d7e454?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Last weekend, I found myself thumbing past Peter Steinberger&#x2019;s monthly reminder for what felt like the fourth time. Continue reading on Medium »

</details>