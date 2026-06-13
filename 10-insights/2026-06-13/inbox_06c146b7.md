---
id: inbox_06c146b7
date: 2026-06-13
source_ref: "[[00-inbox/2026-06-13/0336-medium-tag-claude-built-two-ai-second-brains-with-the-same-c009]]"
title: "Built Two AI Second Brains With the Same Documents — One Gave Better Answers. Here’s Why."
url: https://medium.com/@dksingh0429/built-two-ai-second-brains-with-the-same-documents-one-gave-better-answers-heres-why-6e96483935a8?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-06-13T02:40:57+00:00
fetched_at: 2026-06-13T03:50:55.234501+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者使用相同來源文件建構兩套對立知識庫架構，進行實驗比較。「金庫 A（資料庫型）」採用嚴格結構化：SCHEMA.md 定義筆記類型、YAML 前置資料、剛性命名規則（ps-client-topic.md）與強制分類。「金庫 B（堆積型）」最小化結構：純 Markdown 基本標題、無前置資料、鬆散命名與零儀式。兩者均本機 Obsidian 運行且整合 Claude Code。關鍵發現：針對客戶工作坊工具適用性的相同問題，金庫 B 提供準確建議（工具 X 的元資料引擎適用舊式 BI 報告），而金庫 A 推理正確但結論錯誤（遺漏一份 Teams 聊天提及的工具應用）。核心洞察：「完整度勝過結構」—單一分散文件比美整理卻不完整的金庫更關鍵。"
key_points:
  - "知識完整度 > 組織優雅度：金庫 B 的一份非正式 Teams 聊天記錄翻轉了分析結論，證明資訊可用性比架構設計優先級更高，LLM 會從完整不完美的資料推導正確結論"
  - "漸進式結構化策略：<50 筆記→擁抱無結構快速捕捉；100-300→逐步強化命名與分類；300+ 筆記→嚴格架構強制執行，避免早期過度設計導致捨入門檻"
  - "真正關鍵因素：單一真實來源（避免冗餘矛盾）、可預測的小寫連字號前置命名（高效查詢）、知識新鮮度隔離（長期 vs 易變資料）、來源追蹤時間戳（衝突解決），與人類視覺格式無關"
tags: [knowledge-vault-architecture, obsidian-systems, ai-retrieval, claude-code-integration, completeness-over-structure]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## Built Two AI Second Brains With the Same Documents — One Gave Better Answers. Here’s Why.

作者使用相同來源文件建構兩套對立知識庫架構，進行實驗比較。「金庫 A（資料庫型）」採用嚴格結構化：SCHEMA.md 定義筆記類型、YAML 前置資料、剛性命名規則（ps-client-topic.md）與強制分類。「金庫 B（堆積型）」最小化結構：純 Markdown 基本標題、無前置資料、鬆散命名與零儀式。兩者均本機 Obsidian 運行且整合 Claude Code。關鍵發現：針對客戶工作坊工具適用性的相同問題，金庫 B 提供準確建議（工具 X 的元資料引擎適用舊式 BI 報告），而金庫 A 推理正確但結論錯誤（遺漏一份 Teams 聊天提及的工具應用）。核心洞察：「完整度勝過結構」—單一分散文件比美整理卻不完整的金庫更關鍵。

### 重點
- 知識完整度 > 組織優雅度：金庫 B 的一份非正式 Teams 聊天記錄翻轉了分析結論，證明資訊可用性比架構設計優先級更高，LLM 會從完整不完美的資料推導正確結論
- 漸進式結構化策略：<50 筆記→擁抱無結構快速捕捉；100-300→逐步強化命名與分類；300+ 筆記→嚴格架構強制執行，避免早期過度設計導致捨入門檻
- 真正關鍵因素：單一真實來源（避免冗餘矛盾）、可預測的小寫連字號前置命名（高效查詢）、知識新鮮度隔離（長期 vs 易變資料）、來源追蹤時間戳（衝突解決），與人類視覺格式無關

**原文：** [medium-tag-claude](https://medium.com/@dksingh0429/built-two-ai-second-brains-with-the-same-documents-one-gave-better-answers-heres-why-6e96483935a8?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

An experiment in structuring knowledge vaults for Claude, with a hard verdict and an architectural build guide for both approaches. Continue reading on Medium »

</details>