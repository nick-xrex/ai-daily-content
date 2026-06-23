---
id: inbox_31a8dcd8
date: 2026-06-22
source_ref: "[[00-inbox/2026-06-22/2221-substack-lennys-newsletter-how-claude-mythos-found-a-15-year-old-bu-f837]]"
title: "How Claude Mythos found a 15-year-old bug in Mozilla Firefox | Brian Grinstead"
url: https://www.lennysnewsletter.com/p/how-claude-mythos-found-a-15-year
source: substack-lennys-newsletter
published_at: 2026-06-22T12:03:06+00:00
fetched_at: 2026-06-23T00:36:11.243995+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Mozilla 工程師 Brian Grinstead 通過 AI 輔助系統在一個月內完成了 423 項安全修復，展示了規模化的自動化潛力。該方案採用 goal-loop harness（目標迴圈框架），將手工流程自動化並引入模型輔助。然而，Grinstead 強調模型本身只是故事的一部分，人類工程師的指導、篩選和驗證同樣不可或缺。這揭示了 AI 協作的真相：不是模型取代人，而是人機分工優化。此案例對依賴大量重複修復的團隊（如安全、基礎設施）具有參考價值，可借鑑 goal-loop harness 的框架設計。"
key_points:
  - "423 項安全修復在 1 個月內完成，展示 AI 輔助開發的規模效應"
  - "Goal-loop harness 框架的實踐應用，結合 AI 生成與人類驗證的分工"
  - "核心洞見：模型不是全部，人類工程師的指導、篩選、驗證在 AI 協作中同樣關鍵"
tags: [goal-loop-harness, security-fixes, ai-assisted-development, mozilla]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## How Claude Mythos found a 15-year-old bug in Mozilla Firefox | Brian Grinstead

Mozilla 工程師 Brian Grinstead 通過 AI 輔助系統在一個月內完成了 423 項安全修復，展示了規模化的自動化潛力。該方案採用 goal-loop harness（目標迴圈框架），將手工流程自動化並引入模型輔助。然而，Grinstead 強調模型本身只是故事的一部分，人類工程師的指導、篩選和驗證同樣不可或缺。這揭示了 AI 協作的真相：不是模型取代人，而是人機分工優化。此案例對依賴大量重複修復的團隊（如安全、基礎設施）具有參考價值，可借鑑 goal-loop harness 的框架設計。

### 重點
- 423 項安全修復在 1 個月內完成，展示 AI 輔助開發的規模效應
- Goal-loop harness 框架的實踐應用，結合 AI 生成與人類驗證的分工
- 核心洞見：模型不是全部，人類工程師的指導、篩選、驗證在 AI 協作中同樣關鍵

**原文：** [substack-lennys-newsletter](https://www.lennysnewsletter.com/p/how-claude-mythos-found-a-15-year)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Watch now | &#127897;&#65039;423 security fixes in one month: Brian Grinstead (Mozilla) shows the goal-loop harness behind it, and why the model was only half the story

</details>