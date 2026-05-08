---
id: inbox_ec87a325
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-localllama-11-67-arc-agi-2-local-eval-on-a-single-4-fbe2]]"
title: "11.67% ARC-AGI-2 Local Eval on a Single 4090: The TOPAS Recursive Architecture"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t6n97x/1167_arcagi2_local_eval_on_a_single_4090_the/
source: reddit-localllama
published_at: 2026-05-07T20:56:47+00:00
fetched_at: 2026-05-08T08:07:35.885531+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者在單 RTX 4090 上訓練了 100M 參數的 TOPAS 遞迴架構模型，在本地評估達 36% ARC-AGI-2 成績，公開排行榜因為推理超時邏輯設置過高而只有 11.67%。團隊強調此架構展示了生物記憶模型結合深層遞迴推理可讓小模型在複雜推理任務上超越自身計算能力等級。預計透過時間管理優化，明天可達 20% 成績；模型仍在訓練的 Grokking 階段，團隊樂觀估計 3-5 週內能達到重大突破。"
key_points:
  - "100M 參數模型在單消費級 GPU (RTX 4090) 上達 36% 本地評估、11.67% 公開排行榜（因推理超時導出 null 結果）"
  - "TOPAS 遞迴架構用深層推理迴圈替代模型規模堆砌，展示小模型通過架構創新可突破計算能力限制"
  - "時間管理邏輯調整是決定遞迴推理效果的關鍵因素，優化後預期可翻倍成績至 ~20%"
tags: [arc-agi-2, recursive-reasoning, small-models, consumer-hardware]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## 11.67% ARC-AGI-2 Local Eval on a Single 4090: The TOPAS Recursive Architecture

開發者在單 RTX 4090 上訓練了 100M 參數的 TOPAS 遞迴架構模型，在本地評估達 36% ARC-AGI-2 成績，公開排行榜因為推理超時邏輯設置過高而只有 11.67%。團隊強調此架構展示了生物記憶模型結合深層遞迴推理可讓小模型在複雜推理任務上超越自身計算能力等級。預計透過時間管理優化，明天可達 20% 成績；模型仍在訓練的 Grokking 階段，團隊樂觀估計 3-5 週內能達到重大突破。

### 重點
- 100M 參數模型在單消費級 GPU (RTX 4090) 上達 36% 本地評估、11.67% 公開排行榜（因推理超時導出 null 結果）
- TOPAS 遞迴架構用深層推理迴圈替代模型規模堆砌，展示小模型通過架構創新可突破計算能力限制
- 時間管理邏輯調整是決定遞迴推理效果的關鍵因素，優化後預期可翻倍成績至 ~20%

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t6n97x/1167_arcagi2_local_eval_on_a_single_4090_the/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I'm not sure too many people care about the ARC-AGI-2 competition anymore, but still...I thought some might find this interesting. They're running it one last time this year. Everyone is currently leaderboard-stuffing using the winning open-source code from last year. That's why if you take a peak it's really just the same scores clogging it up. We're doing something a bit different though, building a highly efficient, deep-recursion model from scratch. We just hit 11.67% on the public LB, but that's with a massive asterisk. We don't have a cluster. We have one RTX 4090 . And we're only 14 days or so into training a 100m parameter model. Locally, this checkpoint actually hit 36%. On the Kaggle submission, our TTT is computationally heavy because of the recursive loops. To avoid a total submission timeout, we set the thresholds too high, and the model ended up outputting [] (null) for nearly half the puzzles...hence the 11.67%. We're trying to show that ARC isn't just a Compute War, but an architecture war. Small models using biological memory models can punch way above their weight class if they can handle the reasoning loops. We're tuning the time-management logic tonight and expect to put a 20% score up tomorrow once we let the model actually finish the thought process. And beyond that...the actual model is still in training, in the Grokking phase. We strongly believe that if we give it another 3-5 weeks to fully train we could drop something really groundbreaking on that leaderboard. If you're interested in how we're scaling recursive reasoning on consumer metal, we'd love to answer questions about it. &#32; submitted by &#32; /u/Doug_Bitterbot [link] &#32; [comments]

</details>