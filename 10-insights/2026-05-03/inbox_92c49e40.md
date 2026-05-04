---
id: inbox_92c49e40
date: 2026-05-03
source_ref: "[[00-inbox/.../inbox_92c49e40]]"
title: "What a time to be alive from 1tk/sec to 20-100tk/sec for huge models"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t2s7ik/what_a_time_to_be_alive_from_1tksec_to_20100tksec/
source: reddit-localllama
published_at: 2026-05-03T17:46:33+00:00
fetched_at: 2026-05-04T14:22:21.938923+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本地 LLM 推理性能在 2 年內實現飛躍式進展。2 年前 Llama 405B Q4 K M 在 1.2 token/sec，當前同等硬體可運行 Qwen 3.5-397B、DeepSeek v4 Flash、MiniMax 2.7 等最新模型於 30-100 token/sec，性能提升 25-83 倍。幾百美元硬體即可在家運行 Qwen 3.6-36B 於 50 token/sec。這一轉變使超大模型本地部署從理想變為經濟可行，重新定義推理架構選擇——從雲端轉向本地邊緣部署。社群持續投入的「看似無謂」實驗正逐步實現 AGI 時代的本地運行能力。"
key_points:
  - "同等硬體性能從 1.2 tk/sec（Llama 405B Q4）躍升至 30-100 tk/sec（新模型），提升 25-83 倍"
  - "Qwen 3.6-36B 可在家庭硬體達 50 tk/sec，超大模型本地部署成本驟降"
  - "性能/成本拐點已達，推動從雲端推理向邊緣本地部署轉移"
tags: [local-inference, performance, qwen, deepseek, token-throughput]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## What a time to be alive from 1tk/sec to 20-100tk/sec for huge models

本地 LLM 推理性能在 2 年內實現飛躍式進展。2 年前 Llama 405B Q4 K M 在 1.2 token/sec，當前同等硬體可運行 Qwen 3.5-397B、DeepSeek v4 Flash、MiniMax 2.7 等最新模型於 30-100 token/sec，性能提升 25-83 倍。幾百美元硬體即可在家運行 Qwen 3.6-36B 於 50 token/sec。這一轉變使超大模型本地部署從理想變為經濟可行，重新定義推理架構選擇——從雲端轉向本地邊緣部署。社群持續投入的「看似無謂」實驗正逐步實現 AGI 時代的本地運行能力。

### 重點
- 同等硬體性能從 1.2 tk/sec（Llama 405B Q4）躍升至 30-100 tk/sec（新模型），提升 25-83 倍
- Qwen 3.6-36B 可在家庭硬體達 50 tk/sec，超大模型本地部署成本驟降
- 性能/成本拐點已達，推動從雲端推理向邊緣本地部署轉移

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t2s7ik/what_a_time_to_be_alive_from_1tksec_to_20100tksec/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# What a time to be alive from 1tk/sec to 20-100tk/sec for huge models

<!-- SC_OFF --><div class="md"><p><a href="https://www.reddit.com/r/LocalLLaMA/comments/1eb6to7/llama_405b_q4_k_m_quantization_running_locally/">https://www.reddit.com/r/LocalLLaMA/comments/1eb6to7/llama_405b_q4_k_m_quantization_running_locally/</a></p> <p><a href="https://www.reddit.com/r/LocalLLaMA/comments/1ebbgkr/llama_31_405b_q5_k_m_running_on_amd_epyc_9374f/">https://www.reddit.com/r/LocalLLaMA/comments/1ebbgkr/llama_31_405b_q5_k_m_running_on_amd_epyc_9374f/</a> </p> <p>Llama405b q4 at 1.2tk/sec 2 years ago was something to be excited about.</p> <p>That same hardware will now run HUGE state of the art models (kimik2.6, deepseekv4flash, minimax2.7, step3.5flash, qwen3.5-397b) at 30tk-100tk/sec while crushing llama405b. :-/</p> <p>I recall folks asking why anyone would want to run Llama405b at 1.2/tk, etc. My answer when folks asked me was that I wanted to be ready for when AGI arrived. If it meant being able to run my own super AI at 1tk/sec I wanted that option. It turned out better than I could have ever imagined, we do have super AGI and we can run them cheap and fast. </p> <p>Putting aside the huge models, for a few hundred $ you could run qwen3.6-36b at 50tk/sec at home. So to my fellow local llama nuts, stay crazy, keep experimenting, ignore the naysayers, all the &quot;stupid&quot;, &quot;waste of time&quot; experiments are paying off.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/segmond"> /u/segmond </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2s7ik/what_a_time_to_be_alive_from_1tksec_to_20100tksec/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2s7ik/what_a_time_to_be_alive_from_1tksec_to_20100tksec/">[comments]</a></span>

</details>