---
id: inbox_f7c004de
date: 2026-08-09
source_ref: "[[00-inbox/2026-08-09/2311-medium-tag-claude-stochastic-where-it-doesnt-matter-why-ll-3ad3]]"
title: "Stochastic Where It Doesn’t Matter: Why LLMs Aren’t Creative, and How We Built a Skill for It in..."
url: https://medium.com/@fernando.dougnac/stochastic-where-it-doesnt-matter-why-llms-aren-t-creative-and-how-we-built-a-skill-for-it-in-d089754bdafa?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-08-09T20:06:32+00:00
fetched_at: 2026-08-10T06:02:55.638203+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文深入探討 LLM 創意能力的根本限制。作者與 Claude 對話，從 decision tree 的隨意提問出發，逐步診斷問題——LLM 的隨機性（stochasticity）在創意任務中表現不足，需要特殊設計補償。文章記錄完整迭代過程：問題識別 → Claude 協作 → 設計測試技能 → eval data 驗證。最終產出一個可量化檢驗的創意技能解決方案。這是難得的 LLM 能力邊界案例研究，具有實驗驗證支持。"
key_points:
  - "LLM 的確定性不足vs隨機性過度：隨機性在創意場景中無法自動解決創意問題"
  - "通過 Claude 對話從問題診斷→方案設計→eval 驗證的完整工作流"
  - "eval data 定量支持：提升創意技能效果是可測量的"
tags: [llm-limitations, creativity-systems, stochasticity, eval-methodology]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Stochastic Where It Doesn’t Matter: Why LLMs Aren’t Creative, and How We Built a Skill for It in...

本文深入探討 LLM 創意能力的根本限制。作者與 Claude 對話，從 decision tree 的隨意提問出發，逐步診斷問題——LLM 的隨機性（stochasticity）在創意任務中表現不足，需要特殊設計補償。文章記錄完整迭代過程：問題識別 → Claude 協作 → 設計測試技能 → eval data 驗證。最終產出一個可量化檢驗的創意技能解決方案。這是難得的 LLM 能力邊界案例研究，具有實驗驗證支持。

### 重點
- LLM 的確定性不足vs隨機性過度：隨機性在創意場景中無法自動解決創意問題
- 通過 Claude 對話從問題診斷→方案設計→eval 驗證的完整工作流
- eval data 定量支持：提升創意技能效果是可測量的

**原文：** [medium-tag-claude](https://medium.com/@fernando.dougnac/stochastic-where-it-doesnt-matter-why-llms-aren-t-creative-and-how-we-built-a-skill-for-it-in-d089754bdafa?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A dialogue with Claude that started with a casual question about decision trees and ended with a tested skill. With eval data, a flat tire&#x2026; Continue reading on Medium »

</details>