---
id: inbox_beabc781
date: 2026-05-10
source_ref: "[[00-inbox/2026-05-10/0150-reddit-localllama-how-does-llama-server-pick-which-moe-exp-1541]]"
title: "How does llama-server pick which MoE experts go on the GPU and which stay on the CPU?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t9fy74/how_does_llamaserver_pick_which_moe_experts_go_on/
source: reddit-localllama
published_at: 2026-05-10T19:11:08+00:00
fetched_at: 2026-05-11T01:57:29.144031+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "此項為 Reddit 使用者提出的技術問題（MoE model 分散推理時 expert GPU/CPU placement 優化），不符合新聞/分析內容摘要範圍。"
key_points:
  - "MoE model 分散推理的 GPU/CPU placement 是效能優化關鍵"
tags: [moe-models, distributed-inference]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## How does llama-server pick which MoE experts go on the GPU and which stay on the CPU?

此項為 Reddit 使用者提出的技術問題（MoE model 分散推理時 expert GPU/CPU placement 優化），不符合新聞/分析內容摘要範圍。

### 重點
- MoE model 分散推理的 GPU/CPU placement 是效能優化關鍵

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t9fy74/how_does_llamaserver_pick_which_moe_experts_go_on/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

If you are using a MoE model that does not fully fit in your GPU, some of the experts must stay on the CPU. Putting the experts that you will actually need on the GPU will give you GPU inference speeds. But guessing entirely incorrectly will only give you CPU inference speeds. Guessing well is probably easy -- the experts you most commonly used before are the ones that you'll probably need. But I wonder if llama-server uses heuristics like this? &#32; submitted by &#32; /u/we_are_mammals [link] &#32; [comments]

</details>