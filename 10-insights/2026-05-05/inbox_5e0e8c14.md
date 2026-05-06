---
id: inbox_5e0e8c14
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_5e0e8c14]]"
title: "Train Your Own LLM from Scratch"
url: https://github.com/angelos-p/llm-from-scratch
source: hackernews
published_at: 2026-05-05T04:09:17+00:00
fetched_at: 2026-05-06T13:37:09.059126+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Angelos P 開源教學專案：在單台筆記本上從零手寫 GPT 訓練管道。模型規模 ~10M 參數，可在 Apple Silicon (M3 Pro) 上 45 分鐘內訓練完成，支援 NVIDIA CUDA 與 CPU 後端；以莎士比亞文本為資料集。課程分 6 部分：字元級 tokenizer、Transformer 架構（embedding、self-attention、layer norm、MLP）、AdamW 訓練循環、採樣推理、完整整合、競賽。強調親手寫每一個元件（不依賴高階抽象），深化對 LLM 內部機制的理解。設計目標是單個工作坊時間內完成（<1 小時）。"
key_points:
  - "~10M 參數 GPT 在消費級筆記本 (M3 Pro / NVIDIA) 上 <1 小時訓練；Google Colab 也支援，零 GPU 購買門檻"
  - "6 個模塊遞進式構建：character tokenizer (vocab_size=65)、6 層 Transformer、AdamW + LR scheduling、temperature/top-k 生成、數據與超參調試"
  - "教學設計移植自 nanoGPT 思想但精簡至本質；強調手寫每個組件而非調用黑箱，適合想深入理解 transformer 與 training loop 的初學者"
tags: [llm-training, educational-project, transformer, distributed-learning, hands-on]
topics: [foundation_models.gpt]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Train Your Own LLM from Scratch

Angelos P 開源教學專案：在單台筆記本上從零手寫 GPT 訓練管道。模型規模 ~10M 參數，可在 Apple Silicon (M3 Pro) 上 45 分鐘內訓練完成，支援 NVIDIA CUDA 與 CPU 後端；以莎士比亞文本為資料集。課程分 6 部分：字元級 tokenizer、Transformer 架構（embedding、self-attention、layer norm、MLP）、AdamW 訓練循環、採樣推理、完整整合、競賽。強調親手寫每一個元件（不依賴高階抽象），深化對 LLM 內部機制的理解。設計目標是單個工作坊時間內完成（<1 小時）。

### 重點
- ~10M 參數 GPT 在消費級筆記本 (M3 Pro / NVIDIA) 上 <1 小時訓練；Google Colab 也支援，零 GPU 購買門檻
- 6 個模塊遞進式構建：character tokenizer (vocab_size=65)、6 層 Transformer、AdamW + LR scheduling、temperature/top-k 生成、數據與超參調試
- 教學設計移植自 nanoGPT 思想但精簡至本質；強調手寫每個組件而非調用黑箱，適合想深入理解 transformer 與 training loop 的初學者

**原文：** [hackernews](https://github.com/angelos-p/llm-from-scratch)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Train Your Own LLM from Scratch

</details>