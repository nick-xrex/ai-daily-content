---
id: inbox_194be923
date: 2026-06-01
source_ref: "[[00-inbox/2026-06-01/2246-medium-tag-llm-hallucination-resistance-part-2-7c00]]"
title: "Hallucination Resistance, Part 2"
url: https://medium.com/@melihzgvnc/hallucination-resistance-part-2-f8034aeebbc7?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-06-01T16:55:00+00:00
fetched_at: 2026-06-01T22:57:44.513190+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章第二部分聚焦**監督微調（SFT）**作為後訓練方法減少 LLM 幻覺。三大後訓練策略：持續預訓練（CPT）注入新知識、SFT 修改行為、偏好調整對齐人類意圖。SFT 使用標記 QA 對示範忠實答案或適當拒絕。低秩適應（LoRA）訓練「少於 1% 的參數」透過可訓練低秩矩陣，模組化適配器可插拔。訓練最佳化：梯度累積、檢點化、學習率 1e-4～2e-4（7B-14B 模型），自訂資料整理器移除衝突梯度。核心目標：改變模型如何處理檢索資訊而非注入新知識。"
key_points:
  - "SFT + LoRA：監督微調標記 QA 對，低秩適配器學習 <1% 參數，支援模組化插拔"
  - "LoRA 學習率 1e-4～2e-4，梯度累積+檢點化降低計算成本，自訂資料整理防衝突梯度"
  - "SFT 修改模型資訊處理方式而非知識庫，改善忠實度優於追加參數"
tags: [hallucination-resistance, lora-fine-tuning, post-training]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Hallucination Resistance, Part 2

文章第二部分聚焦**監督微調（SFT）**作為後訓練方法減少 LLM 幻覺。三大後訓練策略：持續預訓練（CPT）注入新知識、SFT 修改行為、偏好調整對齐人類意圖。SFT 使用標記 QA 對示範忠實答案或適當拒絕。低秩適應（LoRA）訓練「少於 1% 的參數」透過可訓練低秩矩陣，模組化適配器可插拔。訓練最佳化：梯度累積、檢點化、學習率 1e-4～2e-4（7B-14B 模型），自訂資料整理器移除衝突梯度。核心目標：改變模型如何處理檢索資訊而非注入新知識。

### 重點
- SFT + LoRA：監督微調標記 QA 對，低秩適配器學習 <1% 參數，支援模組化插拔
- LoRA 學習率 1e-4～2e-4，梯度累積+檢點化降低計算成本，自訂資料整理防衝突梯度
- SFT 修改模型資訊處理方式而非知識庫，改善忠實度優於追加參數

**原文：** [medium-tag-llm](https://medium.com/@melihzgvnc/hallucination-resistance-part-2-f8034aeebbc7?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Check out the first part of this blog series Continue reading on Medium »

</details>