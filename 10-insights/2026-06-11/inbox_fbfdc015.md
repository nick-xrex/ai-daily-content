---
id: inbox_fbfdc015
date: 2026-06-11
source_ref: "[[00-inbox/2026-06-11/2200-simon-willison-datasette-1-0a33-fae3]]"
title: "datasette 1.0a33"
url: https://simonwillison.net/2026/Jun/11/datasette/#atom-everything
source: simon-willison
published_at: 2026-06-11T15:26:49+00:00
fetched_at: 2026-06-11T22:06:45.743130+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 1.0a33 alpha 發布，主要改進是將既有的 ?_extra= API 擴展參數模式從 tables 推廣至 queries 和 rows，統一不同資料層級的 API 設計。Simon Willison 展示跨模型開發工作流實踐——使用 Claude Fable 5 在 Claude Code 進行規劃與設計、GPT-5.5 xhigh 在 Codex Desktop 進行程式實現，快速構建自訂 API explorer 工具以示範新功能。該案例說明多模型組合的效率——不同模型各展所長，比單一模型的單純堆砌計算資源更有效。API 模式擴展亦被正式文件化，降低新手使用門檻。"
key_points:
  - "?_extra= 模式擴展至 queries 和 rows，統一 Datasette 跨層級 API 設計"
  - "混合 Claude Fable 5（規劃）與 GPT-5.5 xhigh（實現）快速建立示範工具"
  - "多模型組合效率優於單一模型堆砌資源的實證案例"
tags: [datasette, api-design, multi-model-development, ai-assisted-programming]
topics: [foundation_models.claude, foundation_models.gpt]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 1.0a33

Datasette 1.0a33 alpha 發布，主要改進是將既有的 ?_extra= API 擴展參數模式從 tables 推廣至 queries 和 rows，統一不同資料層級的 API 設計。Simon Willison 展示跨模型開發工作流實踐——使用 Claude Fable 5 在 Claude Code 進行規劃與設計、GPT-5.5 xhigh 在 Codex Desktop 進行程式實現，快速構建自訂 API explorer 工具以示範新功能。該案例說明多模型組合的效率——不同模型各展所長，比單一模型的單純堆砌計算資源更有效。API 模式擴展亦被正式文件化，降低新手使用門檻。

### 重點
- ?_extra= 模式擴展至 queries 和 rows，統一 Datasette 跨層級 API 設計
- 混合 Claude Fable 5（規劃）與 GPT-5.5 xhigh（實現）快速建立示範工具
- 多模型組合效率優於單一模型堆砌資源的實證案例

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/11/datasette/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette 1.0a33 
 This alpha is a significant step on the road to a stable 1.0, finally extending the ?_extra= pattern I introduced in Datasette 1.0a3 to cover queries and rows in addition to tables. That pattern is also now documented ! 
 I wrote a whole lot more about the new release on the Datasette project blog: Datasette 1.0a33 with JSON extras in the API . 
 Because API explorer tools are almost free to build now I had Claude Fable 5 in Claude Code (for the plan ) and GPT-5.5 xhigh in Codex Desktop (for the implementation ) build me this custom extras API explorer to help demonstrate the feature: 
 
 
 
 Tags: projects , datasette , annotated-release-notes , ai-assisted-programming

</details>