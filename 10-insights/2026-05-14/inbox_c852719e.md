---
id: inbox_c852719e
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_c852719e]]"
title: "[MIT] RLCR: Teaching AI models to say \&#34;I&#39;m not sure\&#34;"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tczrop/mit_rlcr_teaching_ai_models_to_say_im_not_sure/
source: reddit-localllama
published_at: 2026-05-14T14:24:40+00:00
fetched_at: 2026-05-18T03:44:23.045254+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "MIT CSAIL 研究發現當代推理模型的過度自信問題—無論答案正確與否都以相同確定性呈現。研究團隊追蹤訓練方式的特定缺陷，提出 RLCR 方法修正此問題，無需犧牲準確性。核心洞察：不確定性缺陷源於訓練導向而非架構限制，可通過改進訓練流程修正。這對決策支持系統、診斷類應用等高信任場景具重要意義。"
key_points:
  - "推理模型過度自信根源於訓練方式特定缺陷，非架構或能力問題"
  - "RLCR 方法實現不確定性校準無損準確性"
  - "框架洞察：訓練導向可直接改變模型行為特性，應用於決策支持與診斷場景"
tags: [uncertainty, calibration, reasoning-models, training-method, mit]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## [MIT] RLCR: Teaching AI models to say \"I'm not sure\"

MIT CSAIL 研究發現當代推理模型的過度自信問題—無論答案正確與否都以相同確定性呈現。研究團隊追蹤訓練方式的特定缺陷，提出 RLCR 方法修正此問題，無需犧牲準確性。核心洞察：不確定性缺陷源於訓練導向而非架構限制，可通過改進訓練流程修正。這對決策支持系統、診斷類應用等高信任場景具重要意義。

### 重點
- 推理模型過度自信根源於訓練方式特定缺陷，非架構或能力問題
- RLCR 方法實現不確定性校準無損準確性
- 框架洞察：訓練導向可直接改變模型行為特性，應用於決策支持與診斷場景

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tczrop/mit_rlcr_teaching_ai_models_to_say_im_not_sure/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# [MIT] RLCR: Teaching AI models to say "I'm not sure"

Confidence is persuasive. In AI systems, it is often misleading. Today's most capable reasoning models share a trait with the loudest voice in the room: They deliver every answer with the same unshakable certainty, whether they're right or guessing. Researchers at MIT's Computer Science and Artificial Intelligence Laboratory (CSAIL) have now traced that overconfidence to a specific flaw in how these models are trained, and developed a method that fixes it without giving up any accuracy. &#32; submitted by &#32; /u/Zyj [link] &#32; [comments]

</details>