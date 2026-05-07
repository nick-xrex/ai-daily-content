---
id: inbox_0f34c61d
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/0114-reddit-localllama-why-people-cares-token-s-in-decoding-mor-4f8a]]"
title: "Why people cares token/s in decoding more?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t5hebz/why_people_cares_tokens_in_decoding_more/
source: reddit-localllama
published_at: 2026-05-06T16:09:24+00:00
fetched_at: 2026-05-07T01:30:59.391199+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "另一位用戶同樣觀察：本地推理瓶頸在 prompt processing 而非 decoding。15+ t/s 生成速度已超越閱讀速度，卻在 Mac mini 上 process 64K tokens 提示耗時 >10 分鐘。質疑為何社群未見 MTP 改善 prefill 的討論，以及不同硬體設定（離散 GPU）是否改變瓶頸。"
key_points:
  - "瓶頸重新定位：Qwen 3.6 27b 在 Mac mini 上 64K tokens 處理 >10 分鐘，成關鍵限制"
  - "生成速度充分論：15+ t/s 已超人工閱讀速，prefill 延遲才是使用者感知障礙"
  - "技術缺口：MTP 等方案重點在 decoding，prefill 優化方向尚未廣泛探討"
tags: [prefill-bottleneck, local-mac-inference, prompt-processing, qwen-3.6]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Why people cares token/s in decoding more?

另一位用戶同樣觀察：本地推理瓶頸在 prompt processing 而非 decoding。15+ t/s 生成速度已超越閱讀速度，卻在 Mac mini 上 process 64K tokens 提示耗時 >10 分鐘。質疑為何社群未見 MTP 改善 prefill 的討論，以及不同硬體設定（離散 GPU）是否改變瓶頸。

### 重點
- 瓶頸重新定位：Qwen 3.6 27b 在 Mac mini 上 64K tokens 處理 >10 分鐘，成關鍵限制
- 生成速度充分論：15+ t/s 已超人工閱讀速，prefill 延遲才是使用者感知障礙
- 技術缺口：MTP 等方案重點在 decoding，prefill 優化方向尚未廣泛探討

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t5hebz/why_people_cares_tokens_in_decoding_more/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>What I've noticed while using local LLM recently is that in most cases, bottlenecks occur not in decoding but in prompt processing. </p> <p>If the prompt processing speed is usable, in most settings (since it takes about 15k when starting based on agentic coding standard) it exceeds 10 tokens per second in generating, doesn't that exceed the speed we can follow with our eyes? </p> <p>I tried to use qwen3.6 27b but it took more than 10m to process 64k prompt on my mac mini, so I rather chose 35b a3b</p> <p>What am I missing? Is the prompt processing speed improved by MTP or other methods? </p> <p>Or is bottleneck just really different with discrete gpu settings?</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Interesting-Print366"> /u/Interesting-Print366 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5hebz/why_people_cares_tokens_in_decoding_more/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t5hebz/why_people_cares_tokens_in_decoding_more/">[comments]</a></span>

</details>