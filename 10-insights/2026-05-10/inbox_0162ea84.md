---
id: inbox_0162ea84
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_0162ea84]]"
title: "Getting a feel for how fast X tokens/second really is."
url: https://www.reddit.com/r/LocalLLaMA/comments/1t99upf/getting_a_feel_for_how_fast_x_tokenssecond_really/
source: reddit-localllama
published_at: 2026-05-10T15:23:08+00:00
fetched_at: 2026-05-11T02:21:09.089147+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "討論本地 LLM 性能表現如何被有意義地量化感受。作者指出 tokens/second 等客觀數字對一般使用者意義不大，建立了互動工具 tokenspeed，支援文字、程式碼和推理推斷等多種任務類型，讓使用者體驗「21 tok/s 實際有多快」這類無法直覺理解的指標。該工具解決了性能數字與實際使用體驗之間的溝通鴻溝。"
key_points:
  - "建立 tokenspeed 工具，將客觀 tokens/second 轉換為主觀使用體驗"
  - "支援多種任務類型測試（text、code、reasoning）"
  - "解決本地 LLM 性能指標難以理解的問題"
tags: [local-llm, performance-metrics, tooling, user-experience]
topics: []
importance: 2
novelty: 3
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Getting a feel for how fast X tokens/second really is.

討論本地 LLM 性能表現如何被有意義地量化感受。作者指出 tokens/second 等客觀數字對一般使用者意義不大，建立了互動工具 tokenspeed，支援文字、程式碼和推理推斷等多種任務類型，讓使用者體驗「21 tok/s 實際有多快」這類無法直覺理解的指標。該工具解決了性能數字與實際使用體驗之間的溝通鴻溝。

### 重點
- 建立 tokenspeed 工具，將客觀 tokens/second 轉換為主觀使用體驗
- 支援多種任務類型測試（text、code、reasoning）
- 解決本地 LLM 性能指標難以理解的問題

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t99upf/getting_a_feel_for_how_fast_x_tokenssecond_really/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Getting a feel for how fast X tokens/second really is.

I love following all your adventures with local LLM setups. Quality and size of the models are important, but so is performance. Numbers don't really convey the experienced speed well, however. If someone claims they run Qwen 3.6-27B at 21 tokens/second, how fast is that? Is 10 tokens/second unusable? I find these numbers objective but meaningless. I built a script that helps me get a subjective feel for these objective numbers. It supports text, code and reasoning + code. https://mikeveerman.github.io/tokenspeed/ &#32; submitted by &#32; /u/MikeNonect [link] &#32; [comments]

</details>