---
id: inbox_fb0bbc1a
date: 2026-05-08
source_ref: "[[00-inbox/.../inbox_fb0bbc1a]]"
title: "new MoE from ai2, EMO"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t7kgy4/new_moe_from_ai2_emo/
source: reddit-localllama
published_at: 2026-05-08T20:57:58+00:00
fetched_at: 2026-05-09T02:53:47.703574+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Allen Institute for AI (AI2) 發布新的 MoE 模型 EMO，規模為 1B active / 14B total，訓練使用 1T tokens。其創新之處在於採用文檔級路由 (document-level routing) 替代傳統的表面模式匹配，使專家自動聚類於健康、新聞等語義領域而非語言表層特徵。這代表 MoE 專家路由策略的新演進方向。"
key_points:
  - "EMO：AI2 推出 1B active / 14B total MoE 模型，基於 1T token 訓練"
  - "文檔級路由策略：專家按語義領域 (health, news 等) 自然聚類，而非淺層特徵匹配，示範路由的語義進化"
  - "新路由思路可應用於其他 MoE 設計，改進專家分工的語義對齐性"
tags: [ai2-emo, moe-routing, document-level, semantic-experts, moe-model]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## new MoE from ai2, EMO

Allen Institute for AI (AI2) 發布新的 MoE 模型 EMO，規模為 1B active / 14B total，訓練使用 1T tokens。其創新之處在於採用文檔級路由 (document-level routing) 替代傳統的表面模式匹配，使專家自動聚類於健康、新聞等語義領域而非語言表層特徵。這代表 MoE 專家路由策略的新演進方向。

### 重點
- EMO：AI2 推出 1B active / 14B total MoE 模型，基於 1T token 訓練
- 文檔級路由策略：專家按語義領域 (health, news 等) 自然聚類，而非淺層特徵匹配，示範路由的語義進化
- 新路由思路可應用於其他 MoE 設計，改進專家分工的語義對齐性

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t7kgy4/new_moe_from_ai2_emo/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# new MoE from ai2, EMO

new MoE release from ai2 - EMO, 1b-active/14b-total trained on 1t tokens interesting thing is document-level routing. experts cluster around domains like health, news, etc. instead of surface patterns models: https://huggingface.co/collections/allenai/emo &#32; submitted by &#32; /u/ghostderp [link] &#32; [comments]

</details>