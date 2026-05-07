---
id: inbox_c0ae1216
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/0114-reddit-localllama-decoupled-attention-from-weights-gemma-4-40cd]]"
title: "Decoupled Attention from Weights - Gemma 4 26B"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t5ap0y/decoupled_attention_from_weights_gemma_4_26b/
source: reddit-localllama
published_at: 2026-05-06T11:56:45+00:00
fetched_at: 2026-05-07T01:30:59.387228+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "提出分布式推理新架構：將注意力層（attention）和模型權重（weights）解耦到不同機器上運行——一台本地機器運行注意力計算（佔幾 GB），另一台便宜伺服器（如 Xeon）存放權重，繞過本地 LLM 規模限制。開源實現 larql 附配套教學影片，已在 Gemma 4 26B 上驗證可行性。"
key_points:
  - "架構創新：Decoupled Attention from Weights，分散計算與存儲到異硬體"
  - "部署方案：本地機存 attention layers（GB 級）、遠端低端伺服器存權重，突破單機記憶體限制"
  - "開源與驗證：GitHub (larql) + YouTube 教學可立即複現，Gemma 4 26B 成功案例"
tags: [distributed-inference, decoupled-attention, architecture-innovation, gemma-4-26b]
topics: []
importance: 4
novelty: 5
insight_quality: 4
insight_type: technique
deep_dive_candidate: true
deep_dive_approved: false
---

## Decoupled Attention from Weights - Gemma 4 26B

提出分布式推理新架構：將注意力層（attention）和模型權重（weights）解耦到不同機器上運行——一台本地機器運行注意力計算（佔幾 GB），另一台便宜伺服器（如 Xeon）存放權重，繞過本地 LLM 規模限制。開源實現 larql 附配套教學影片，已在 Gemma 4 26B 上驗證可行性。

### 重點
- 架構創新：Decoupled Attention from Weights，分散計算與存儲到異硬體
- 部署方案：本地機存 attention layers（GB 級）、遠端低端伺服器存權重，突破單機記憶體限制
- 開源與驗證：GitHub (larql) + YouTube 教學可立即複現，Gemma 4 26B 成功案例

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t5ap0y/decoupled_attention_from_weights_gemma_4_26b/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>Absolutely unbelievably exciting work, split attention (i.e. a couple of GB) onto local machine and the weights onto another local machine (say a cheap Xeon) to basically bypass the scale issue with local LLMs completely!! Repo with functional code: <a href="https://github.com/chrishayuk/larql">https://github.com/chrishayuk/larql</a></p> <p>edit: just found <a href="https://www.youtube.com/watch?v=1jGR4zqpyKA">https://www.youtube.com/watch?v=1jGR4zqpyKA</a> for excellent overview of what's happening here.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/yeah-ok"> /u/yeah-ok </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5ap0y/decoupled_attention_from_weights_gemma_4_26b/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5ap0y/decoupled_attention_from_weights_gemma_4_26b/">[comments]</a></span>

</details>