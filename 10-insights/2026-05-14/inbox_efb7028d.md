---
id: inbox_efb7028d
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_efb7028d]]"
title: "Dropping learning rate fixed my Qlora fine-tune more than anything else i tried"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tcwzl6/dropping_learning_rate_fixed_my_qlora_finetune/
source: reddit-localllama
published_at: 2026-05-14T12:40:39+00:00
fetched_at: 2026-05-18T03:45:18.757741+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reddit 用戶分享 Qlora 微調經驗：用 Llama 3.1 8B 在 8k 樣本分類任務上，將 learning rate 從預設 2e-4 降至 1e-4、epochs 從 3 增加至 5，結合資料清理（移除 1/3 有歧義與標籤錯誤樣本），eval 結果顯著改善。關鍵發現：2e-4 在小數據集上過激，導致第一個 epoch 過擬合後無充足空間收斂；低 learning rate + 更多 epochs 給予更多微調機會。"
key_points:
  - "learning rate 2e-4 → 1e-4、epochs 3 → 5，於 RTX5090 達顯著改善"
  - "小數據集（<10k 樣本）下預設 2e-4 過高，容易第一個 epoch 過擬合"
  - "資料清理（移除標籤錯誤樣本）比單純增加資料量更有效"
tags: [qlora, fine-tuning, learning-rate, llama-3.1, hyperparameter-optimization]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Dropping learning rate fixed my Qlora fine-tune more than anything else i tried

Reddit 用戶分享 Qlora 微調經驗：用 Llama 3.1 8B 在 8k 樣本分類任務上，將 learning rate 從預設 2e-4 降至 1e-4、epochs 從 3 增加至 5，結合資料清理（移除 1/3 有歧義與標籤錯誤樣本），eval 結果顯著改善。關鍵發現：2e-4 在小數據集上過激，導致第一個 epoch 過擬合後無充足空間收斂；低 learning rate + 更多 epochs 給予更多微調機會。

### 重點
- learning rate 2e-4 → 1e-4、epochs 3 → 5，於 RTX5090 達顯著改善
- 小數據集（<10k 樣本）下預設 2e-4 過高，容易第一個 epoch 過擬合
- 資料清理（移除標籤錯誤樣本）比單純增加資料量更有效

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tcwzl6/dropping_learning_rate_fixed_my_qlora_finetune/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Dropping learning rate fixed my Qlora fine-tune more than anything else i tried

Been fine-tuning llama 3.1 8b with Qlora for a classification task using about 8k samples. I was getting bad eval results for a while and kept thinking something was wrong with my data. Tried cleaning the dataset, tried different prompt templates, messed with rank and alpha. Nothing realy changed. Dropped the learning rate from 2e-4 to 1e-4 and bumped epochs from 3 to 5. Ran it on a 5090 I rent on Hyperai since our lab machines are always booked. Completley different results. Same data, same everything else. 2e-4 is just too agressive when your dataset is that small. The model overfits in the first epoch and then just goes in circles for the rest of training. Lower lr gave it more room to converge without blowing past everything. Also ended up cutting about a third of my dataset, mostly mislabeled and ambiguous stuff. Eval got better with less data which yeah yeah everyone says that but its different when you see the numbers yourself lol 2e-4 is the default everywhere and i dont think it works well below a certain size. &#32; submitted by &#32; /u/Scared-Biscotti2287 [link] &#32; [comments]

</details>