---
id: inbox_3b257aab
date: 2026-05-24
source_ref: "[[00-inbox/2026-05-24/0011-medium-tag-llm-i-build-ai-that-actually-works-in-produc-efdb]]"
title: "I Build AI That Actually Works in Production"
url: https://medium.com/@karthikallapiran/i-build-ai-that-actually-works-in-production-579454fd86f7?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-24T17:59:37+00:00
fetched_at: 2026-05-25T00:19:28.918817+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Kartik Allapiran 指出大多數 AI 項目在演示時亮眼卻在生產環境失敗。生產級 AI 需五大基礎：可靠數據檢索、上下文錨定防止幻覺、流式漸進交付、系統可追溯性、迭代推理循環。CodeAgent 運用四層推理結合 AST 靜態分析；PaperMind 雙路混合檢索結合向量和關鍵詞配對與重排序；Resume ATS 證明微調模型超越通用 LLM。核心模式：混合檢索勝單一方法、工具設計品質決定智能體效能、透過架構預防幻覺而非事後補救。"
key_points:
  - "混合檢索(向量+關鍵詞+重排序)勝於單一方法，成為生產級檢索的標準模式"
  - "工具設計品質直接決定智能體效能——劣質工具會放大而非緩解智能體誤差"
  - "預防勝於修復：透過架構設計預防幻覺(如 PaperMind 的預處理降噪)，而非事後檢測"
tags: [production-ai, rag, agent-design, hallucination-prevention]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## I Build AI That Actually Works in Production

Kartik Allapiran 指出大多數 AI 項目在演示時亮眼卻在生產環境失敗。生產級 AI 需五大基礎：可靠數據檢索、上下文錨定防止幻覺、流式漸進交付、系統可追溯性、迭代推理循環。CodeAgent 運用四層推理結合 AST 靜態分析；PaperMind 雙路混合檢索結合向量和關鍵詞配對與重排序；Resume ATS 證明微調模型超越通用 LLM。核心模式：混合檢索勝單一方法、工具設計品質決定智能體效能、透過架構預防幻覺而非事後補救。

### 重點
- 混合檢索(向量+關鍵詞+重排序)勝於單一方法，成為生產級檢索的標準模式
- 工具設計品質直接決定智能體效能——劣質工具會放大而非緩解智能體誤差
- 預防勝於修復：透過架構設計預防幻覺(如 PaperMind 的預處理降噪)，而非事後檢測

**原文：** [medium-tag-llm](https://medium.com/@karthikallapiran/i-build-ai-that-actually-works-in-production-579454fd86f7?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Real systems. Real problems solved. Real impact. Not just notebooks and theory. Continue reading on Medium »

</details>