---
id: inbox_aa28a01b
date: 2026-05-06
source_ref: "[[00-inbox/.../inbox_aa28a01b]]"
title: "Qwen 3.6 27B MTP on v100 32GB: 54 t/s"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t4zu88/qwen_36_27b_mtp_on_v100_32gb_54_ts/
source: reddit-localllama
published_at: 2026-05-06T02:18:44+00:00
fetched_at: 2026-05-06T13:25:41.547412+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者在 NVIDIA V100 32GB GPU 上測試了 Qwen 3.6 27B 模型搭配 am17an 的 MTP（多令牌預測）分支，獲得 54-55 tokens/秒的吞吐量，相比沒有 MTP 的 29-30 t/s 實現了接近 2 倍的加速。使用 q8_0 key-value cache、200k context limit、150W 功率限制。在消耗 50k tokens 後性能降至 40-45 t/s，但在工具調用、多代理任務和程式碼審查中表現良好。"
key_points:
  - "MTP 技術將吞吐量從 29-30 t/s 提升到 54-55 t/s，實現 ~86% 性能提升"
  - "適用於大規模 context 場景（200k cache），但在 50k tokens 後性能衰減至 40-45 t/s"
  - "驗證了 MTP 在 V100 硬件上的實用性，為本地開發者提供了效能參考"
tags: [mtp-optimization, qwen-3.6, local-llm-inference, gpu-benchmark, token-prediction]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen 3.6 27B MTP on v100 32GB: 54 t/s

使用者在 NVIDIA V100 32GB GPU 上測試了 Qwen 3.6 27B 模型搭配 am17an 的 MTP（多令牌預測）分支，獲得 54-55 tokens/秒的吞吐量，相比沒有 MTP 的 29-30 t/s 實現了接近 2 倍的加速。使用 q8_0 key-value cache、200k context limit、150W 功率限制。在消耗 50k tokens 後性能降至 40-45 t/s，但在工具調用、多代理任務和程式碼審查中表現良好。

### 重點
- MTP 技術將吞吐量從 29-30 t/s 提升到 54-55 t/s，實現 ~86% 性能提升
- 適用於大規模 context 場景（200k cache），但在 50k tokens 後性能衰減至 40-45 t/s
- 驗證了 MTP 在 V100 硬件上的實用性，為本地開發者提供了效能參考

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t4zu88/qwen_36_27b_mtp_on_v100_32gb_54_ts/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Qwen 3.6 27B MTP on v100 32GB: 54 t/s

<!-- SC_OFF --><div class="md"><p>Just a quick note that I got a nice result using am17an's MTP branch of llama.cpp on v100 32GB SXM module using one of those pcie card adapters. Pulled and built in one shot, and llama-server ran without a hitch.</p> <p>Tested using am17an's MTP GGUF, q8_0 kv cache and 200k cache limit acting as vscode copilot.</p> <p>29-30 t/s without MTP</p> <p>54-55t/s with MTP, using 150W power limit on the card.</p> <p>Falls to 40-45 t/s after choking down 50k tokens, but doing great with tool calls, sub agents, and made some very insightful code reviews and refactors. </p> <p>Thank you am17an! Can't wait to see this branch mature, this is great stuff.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/m94301"> /u/m94301 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4zu88/qwen_36_27b_mtp_on_v100_32gb_54_ts/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4zu88/qwen_36_27b_mtp_on_v100_32gb_54_ts/">[comments]</a></span>

</details>