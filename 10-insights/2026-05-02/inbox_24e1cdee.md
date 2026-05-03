---
id: inbox_24e1cdee
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-medium-tag-llm-algorithmic-advances-in-rl-tuning-of-lar-f75d]]"
title: "Algorithmic Advances in RL-Tuning of Large Language Models"
url: https://medium.com/@dhananjayashok99/algorithmic-advances-in-rl-tuning-of-large-language-models-26427c74212a?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-02T19:11:48+00:00
fetched_at: 2026-05-03T01:46:29.692327+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "介紹 RL 調優 LLM 的四項算法進展。DAPO（解耦裁剪動態採樣策略優化）進行四項調整：移除顯式 KL 散度項、採差異化裁剪促進探索、濾除全部軌跡失敗或全部成功數據、調整響應長度歸一化。GSPO（群組序列策略優化）改進重要性採樣，從標記級改為序列級視角，將整個序列作為真實軌跡進行裁剪。GEPO 進一步採群組期望進行比值計算，CISPO 回歸 REINFORCE 方法直接裁剪重要性權重並設極高下界防止策略漂移。各算法共同焦點在完善「比值項」（衡量舊新政策差異），逐步從標記級演進到序列級考量，精化裁剪與歸一化策略。"
key_points:
  - "DAPO 四項調整：去除 KL 散度項、差異化裁剪、濾除極端軌跡、調整長度歸一化，改進探索與收斂性"
  - "GSPO 關鍵創新：比值項從標記級升至序列級，將整個序列作為單位進行裁剪，邏輯上更合理"
  - "演進路線清晰：DAPO→GSPO→GEPO→CISPO，逐步精化比值項計算與裁剪策略，層層遞進"
tags: [rl-fine-tuning, algorithm-advances, policy-optimization, llm-training, dapo-gspo]
topics: [foundation_models.claude, foundation_models.gpt]
importance: 3
novelty: 4
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Algorithmic Advances in RL-Tuning of Large Language Models

介紹 RL 調優 LLM 的四項算法進展。DAPO（解耦裁剪動態採樣策略優化）進行四項調整：移除顯式 KL 散度項、採差異化裁剪促進探索、濾除全部軌跡失敗或全部成功數據、調整響應長度歸一化。GSPO（群組序列策略優化）改進重要性採樣，從標記級改為序列級視角，將整個序列作為真實軌跡進行裁剪。GEPO 進一步採群組期望進行比值計算，CISPO 回歸 REINFORCE 方法直接裁剪重要性權重並設極高下界防止策略漂移。各算法共同焦點在完善「比值項」（衡量舊新政策差異），逐步從標記級演進到序列級考量，精化裁剪與歸一化策略。

### 重點
- DAPO 四項調整：去除 KL 散度項、差異化裁剪、濾除極端軌跡、調整長度歸一化，改進探索與收斂性
- GSPO 關鍵創新：比值項從標記級升至序列級，將整個序列作為單位進行裁剪，邏輯上更合理
- 演進路線清晰：DAPO→GSPO→GEPO→CISPO，逐步精化比值項計算與裁剪策略，層層遞進

**原文：** [medium-tag-llm](https://medium.com/@dhananjayashok99/algorithmic-advances-in-rl-tuning-of-large-language-models-26427c74212a?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@dhananjayashok99/algorithmic-advances-in-rl-tuning-of-large-language-models-26427c74212a?source=rss------large_language_models-5"><img src="https://cdn-images-1.medium.com/max/1065/1*UvC_F3ioERtjFAQLcmCtNQ.png" width="1065" /></a></p><p class="medium-feed-snippet">In a previous post, I did a brief overview of RL fundamentals with LLMs in mind&#x2026;</p><p class="medium-feed-link"><a href="https://medium.com/@dhananjayashok99/algorithmic-advances-in-rl-tuning-of-large-language-models-26427c74212a?source=rss------large_language_models-5">Continue reading on Medium »</a></p></div>

</details>