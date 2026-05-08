---
id: inbox_7eff77db
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-localllama-two-related-prompts-different-results-qw-e500]]"
title: "Two related prompts, different results: Qwen 3.5 and Gemma 4 need different prompting than Qwen 3.6"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t6bsil/two_related_prompts_different_results_qwen_35_and/
source: reddit-localllama
published_at: 2026-05-07T14:14:11+00:00
fetched_at: 2026-05-08T08:05:33.124540+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reddit 用戶進行了系統的提示詞工程對比測試，發現不同模型（Qwen 3.5、Qwen 3.6、Gemma 4）對同一問題的短版本和長版本提示詞的反應差異顯著。使用蘋果生意數學問題（預期答案 300）測試，發現 Qwen 3.5 在短提示詞上表現較好，Gemma 4 偏好長版本（將問題理解為商業而非純數學），而 Qwen 3.6 意外地在長版本上表現最差（даже Q8 量化）。有趣的是 IQ2 量化版本表現出乎意料地良好。研究表明類似的模型架構也需要差異化的提示詞策略。"
key_points:
  - "Qwen 3.5 vs 3.6 對相同提示詞的反應差異大，需採用不同的提示詞風格優化"
  - "Gemma 4 更好地將長版本提示詞理解為商業問題而非純數學題，準確率更高"
  - "量化等級（IQ2 vs Q8）影響模型對提示詞上下文的敏感度，需個別調優"
tags: [prompt-engineering, qwen, gemma, model-evaluation, quantization]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Two related prompts, different results: Qwen 3.5 and Gemma 4 need different prompting than Qwen 3.6

Reddit 用戶進行了系統的提示詞工程對比測試，發現不同模型（Qwen 3.5、Qwen 3.6、Gemma 4）對同一問題的短版本和長版本提示詞的反應差異顯著。使用蘋果生意數學問題（預期答案 300）測試，發現 Qwen 3.5 在短提示詞上表現較好，Gemma 4 偏好長版本（將問題理解為商業而非純數學），而 Qwen 3.6 意外地在長版本上表現最差（даже Q8 量化）。有趣的是 IQ2 量化版本表現出乎意料地良好。研究表明類似的模型架構也需要差異化的提示詞策略。

### 重點
- Qwen 3.5 vs 3.6 對相同提示詞的反應差異大，需採用不同的提示詞風格優化
- Gemma 4 更好地將長版本提示詞理解為商業問題而非純數學題，準確率更高
- 量化等級（IQ2 vs Q8）影響模型對提示詞上下文的敏感度，需個別調優

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t6bsil/two_related_prompts_different_results_qwen_35_and/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

With every new model release there's the &quot;better than Opus 6.13&quot; guys vs the &quot;this is so bad, why did they even release it&quot; camp and I'm always wondering which one is using it wrong. So I did a little test with 2 related prompts, 3 models and ran each combination 10 times. Short prompt: Mike grew up as one of 6 siblings and has 3 sisters. He has $25 and bought 5 boxes of apples for his organic apples business. To support him, his siblings also gifted some apples, with each of his brothers giving him 4 boxes and his sisters 2 boxes each. One of the brothers bought the cheap apples for Mike which were not organic, so Mike can't sell them and returned them. In his first week, Mike sold all boxes of apples and using all the money he earned from that bought twice the amount of apples for the second week. How much money would Mike earn in the second week if he was able to sell all of them? Expected Answer: 300. Assumption: shorter prompt = better. The longer version contains more fluff, not more facts. Qwen 3.6 &gt; Qwen 3.5 IQ2 dumb Result: Most wrong answers were assuming &quot;one box is $5&quot; no matter if buying or selling and answered 150 instead of 300 (except Qwen 3.6 IQ2 which, in the longer story, 50% of the time ignored the sibling boxes and said $25*2=$50). Gemma 4 really liked the longer version. With the story around it, Gemma 4 saw it more as a &quot;business&quot; with different buying and selling prices instead of a purely mathematical, assumption based question. Qwen 3.6 performed surprisingly bad with the long prompt, even in Q8. It mostly either missed the business part and said $150 or forgot about the sibling boxes and said $50. IQ2 was surprisingly good I was really surprised by this, turns out there's not just good prompts and bad prompts but even apparently similar models (Qwen 3.5 vs 3.6) can require different prompting styles. For context: the other prompt contains the exact same sentences, but embedded in a longer story: The Organic Apple Enterprise The sun barely peeked over the rolling hills of the valley when Mike was already awake, brewing his morning coffee and lacing up his work boots. The peaceful, quiet calm of the dawn was a stark contrast to the memories of his childhood home. It had always been a loud, energetic household, filled with constant chatter, shared chores, and the occasional battle over the television remote. Mike grew up as one of 6 siblings and has 3 sisters. Growing up in such a bustling environment taught him the value of hard work, compromise, and the sheer determination required to stand out... The full long prompt can be found here The full data of the comparison (token in- and output numbers, model answers etc): https://evaluateai.ai/app/comparisons/7d1baf23-49d0-484b-8c59-854dcc2e4f64/results/ Disclaimer: that's my website, I created it specifically to compare (local) LLMs. You can create one or several prompts, point it at your local endpoint and then compare the results. &#32; submitted by &#32; /u/Excellent_Jelly2788 [link] &#32; [comments]

</details>