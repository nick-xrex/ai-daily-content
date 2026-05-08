---
id: inbox_ff5f53b1
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0737-medium-tag-claude-you-gave-the-model-more-context-to-fix-t-1390]]"
title: "You gave the model more context to fix the problem. More context was the problem."
url: https://medium.com/@stratoatlas/you-gave-the-model-more-context-to-fix-the-problem-more-context-was-the-problem-a5fae8844122?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-08T06:12:27+00:00
fetched_at: 2026-05-08T07:58:45.377960+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章挑戰 AI 開發常見誤解：認為模型性能在大 context 下衰退源於資訊不足。實際根本原因是建築性的—— transformer attention 非均勻分布。Aider 創作者 Paul Gauthier 驗證發現 200K token window 在 GPT-4o、Claude Sonnet、DeepSeek 上並「在實踐中無用」。核心機制是「信號稀釋」：中間位置詞元的注意力弱於邊界，隨著 token 增加信噪比持續惡化（非突變懸崖）。建議建築性轉變：分離 loading contract 和 reasoning contract，以 attention 位置而非覆蓋進行設計。結論：「context window 不是瓶頸，attention 才是。」"
key_points:
  - "實驗驗證 (Paul Gauthier)：200K+ context 在主流模型上無效能提升，大 window 不等於大理解力"
  - "Attention 機制事實：中間位置信號衰減是 transformer 建築性質，非資訊問題，增加 token 反而加重信雜比"
  - "設計反轉：不應以「覆蓋更多代碼」的思路回應衰退，改為分離 loading 和 reasoning 契約、優先化注意力位置"
tags: [context-window, attention-mechanism, llm-architecture, signal-dilution, transformer]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## You gave the model more context to fix the problem. More context was the problem.

文章挑戰 AI 開發常見誤解：認為模型性能在大 context 下衰退源於資訊不足。實際根本原因是建築性的—— transformer attention 非均勻分布。Aider 創作者 Paul Gauthier 驗證發現 200K token window 在 GPT-4o、Claude Sonnet、DeepSeek 上並「在實踐中無用」。核心機制是「信號稀釋」：中間位置詞元的注意力弱於邊界，隨著 token 增加信噪比持續惡化（非突變懸崖）。建議建築性轉變：分離 loading contract 和 reasoning contract，以 attention 位置而非覆蓋進行設計。結論：「context window 不是瓶頸，attention 才是。」

### 重點
- 實驗驗證 (Paul Gauthier)：200K+ context 在主流模型上無效能提升，大 window 不等於大理解力
- Attention 機制事實：中間位置信號衰減是 transformer 建築性質，非資訊問題，增加 token 反而加重信雜比
- 設計反轉：不應以「覆蓋更多代碼」的思路回應衰退，改為分離 loading 和 reasoning 契約、優先化注意力位置

**原文：** [medium-tag-claude](https://medium.com/@stratoatlas/you-gave-the-model-more-context-to-fix-the-problem-more-context-was-the-problem-a5fae8844122?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Live StratoAtlas Case Continue reading on Medium »

</details>