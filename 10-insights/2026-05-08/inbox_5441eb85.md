---
id: inbox_5441eb85
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0151-reddit-localllama-mtp-is-all-about-acceptance-rate-14e4]]"
title: "MTP is all about acceptance rate"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t7mdrl/mtp_is_all_about_acceptance_rate/
source: reddit-localllama
published_at: 2026-05-08T22:11:38+00:00
fetched_at: 2026-05-09T02:26:09.332124+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用户通过在Gemma4-26b-a4b上测试MTP（Multi-Token Prediction）发现其效能严格取决于draft token的acceptance rate。代码生成场景acceptance率66%时获得1.53×加速（75→114.8 tok/s），但长文本31%acceptance率仅0.95×，JSON输出8%acceptance率直接反向减速（51.3→25.6 tok/s）。关键发现：acceptance rate低于50%时MTP的推理开销会完全抵消加速收益。这揭示MTP并非通用加速方案。"
key_points:
  - "MTP收益与workload特性强相关：代码生成(66% accept)1.53×快，长文本(31%)无加速，JSON(8%)反向减速50%"
  - "临界阈值：acceptance rate低于50%时，MTP的推理开销杀死整体性能收益"
  - "测试环境M4 Max Studio+Gemma4-26b-a4b，结构化输出关闭（mlx-vlm无json_schema支持）"
tags: [mtp, multi-token-prediction, acceptance-rate, performance-analysis, speculative-decoding]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## MTP is all about acceptance rate

用户通过在Gemma4-26b-a4b上测试MTP（Multi-Token Prediction）发现其效能严格取决于draft token的acceptance rate。代码生成场景acceptance率66%时获得1.53×加速（75→114.8 tok/s），但长文本31%acceptance率仅0.95×，JSON输出8%acceptance率直接反向减速（51.3→25.6 tok/s）。关键发现：acceptance rate低于50%时MTP的推理开销会完全抵消加速收益。这揭示MTP并非通用加速方案。

### 重點
- MTP收益与workload特性强相关：代码生成(66% accept)1.53×快，长文本(31%)无加速，JSON(8%)反向减速50%
- 临界阈值：acceptance rate低于50%时，MTP的推理开销杀死整体性能收益
- 测试环境M4 Max Studio+Gemma4-26b-a4b，结构化输出关闭（mlx-vlm无json_schema支持）

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t7mdrl/mtp_is_all_about_acceptance_rate/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

So I was very excited about the MTP stuff especially since Gemma4 has become my &quot;daily driver&quot; for some stuff. I grabbed the latest mlx-vlm and did some tests and found it disappointing. Workload MTP off MTP on Result Draft accept rate Code generation 75 tok/s 114.8 tok/s 1.53× faster 66% of slots Long-form prose 75 tok/s 71.1 tok/s 0.95× (wash) 31% of slots JSON output 51.3 tok/s 25.6 tok/s 0.50× slower 8% of slots Code generation was the typical &quot;Write some python functions to do X&quot; Long form prose was &quot;Write an 800 word essay on paper money in the Tang Dynasty&quot; JSON output was my core use case where I'm handing the LLM a list of items, asking it to group them by similarity according to some rules and then get them back in a structured output*. So if you want to use it for local coding, MTP is great. If you're not, maybe not so hot. My regression testing seems to indicate that once token acceptance dips below 50% the overhead kills the benefit. All this on an M4 Max Studio w/Gemma4-26b-a4b *Bonus for you hackers: Gemma's JSON structure instruction following is pretty good and I find using structured output to be about a 20% hit to token generation. It is faster to just accept a little bit of sloppy JSON and massage it at runtime; so all this is with json_schema off which mlx-vlm doesn't support for spec-decode anyway &#32; submitted by &#32; /u/Hydroskeletal [link] &#32; [comments]

</details>