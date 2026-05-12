---
id: inbox_cf1cb479
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/1800-reddit-localllama-the-qwen-3-6-35b-a3b-hype-is-real-42fc]]"
title: "The Qwen 3.6 35B A3B hype is real!!!"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t9whrt/the_qwen_36_35b_a3b_hype_is_real/
source: reddit-localllama
published_at: 2026-05-11T07:51:34+00:00
fetched_at: 2026-05-11T18:11:59.432469+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本地開源大模型社群的實測發現，Qwen 3.6 35B A3B、Qwen 3.6 27B、Gemma 4 26B A4B 與 Nemotron 3 Nano 等新型號採用了 gated delta net、hybrid Mamba2、sliding window attention 等新穎的 context 擴展技術，使其對複雜程式碼與學術論文的理解能力相比數月前的小模型大幅提升。測試者基於學術程式碼理解的實測評估，認為 Qwen 3.6 35B A3B 版本表現最優；同時主張這些本地模型配合聰慧的人類操作者，在多數場景可能超越 Claude Opus 4.7 單獨使用的表現，點出人機組合相對單一商業模型的優勢。"
key_points:
  - "Qwen 3.6 35B A3B、Qwen 3.6 27B、Gemma 4 26B A4B、Nemotron 3 Nano 採用新型 context 擴展技術（gated delta net、hybrid Mamba2、sliding window attention）"
  - "35B 級本地模型相比數月前 Devstral Small 2，對學術程式碼理解能力躍升"
  - "開發者實測評估：本地模型+人類配合 > Opus 4.7 單獨使用"
tags: [local-llm, qwen, context-extension, benchmarking, model-comparison]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## The Qwen 3.6 35B A3B hype is real!!!

本地開源大模型社群的實測發現，Qwen 3.6 35B A3B、Qwen 3.6 27B、Gemma 4 26B A4B 與 Nemotron 3 Nano 等新型號採用了 gated delta net、hybrid Mamba2、sliding window attention 等新穎的 context 擴展技術，使其對複雜程式碼與學術論文的理解能力相比數月前的小模型大幅提升。測試者基於學術程式碼理解的實測評估，認為 Qwen 3.6 35B A3B 版本表現最優；同時主張這些本地模型配合聰慧的人類操作者，在多數場景可能超越 Claude Opus 4.7 單獨使用的表現，點出人機組合相對單一商業模型的優勢。

### 重點
- Qwen 3.6 35B A3B、Qwen 3.6 27B、Gemma 4 26B A4B、Nemotron 3 Nano 採用新型 context 擴展技術（gated delta net、hybrid Mamba2、sliding window attention）
- 35B 級本地模型相比數月前 Devstral Small 2，對學術程式碼理解能力躍升
- 開發者實測評估：本地模型+人類配合 > Opus 4.7 單獨使用

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t9whrt/the_qwen_36_35b_a3b_hype_is_real/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

My personal test for small local LLM intelligence is to check whether a model has any ability to understand the code that I write for my own academic research. My research is on some pretty niche topics and I doubt that anything like it is substantively present in the training sets for LLMs. A few months ago, small local models' ability to understand my code was nominal at best with Devstral Small 2 being the top performer . However, several small open weight models now have methods of accommodating fairly long contexts (gated delta net, hybrid Mamba2, sliding window attention) which makes them extremely smarter . I can now feed a model an entire academic paper along with accompanying code and ask it to use the paper to work out what the code is doing. I just spent a couple days experimenting with: Qwen 3.6 35B A3B Qwen 3.6 27B Gemma 4 26B A4B Nemotron 3 Nano All of them were able to comprehend my code significantly better than what any small local model could do a few months ago. I did try Devstral Small 2 since I recently went from a single 16GB graphics card to two; however, I simply couldn't fit the long context in 32GB of ram. I hope Mistral releases a new small model with a gated delta net, because I think it could take the throne. These are my detailed findings from asking local models to explain how my code maps to the research paper it corresponds to. TLDR: All four models listed above are incredibly capable local models, with Qwen 3.6 35B A3B standing out as the best. I'm also inclined to think that an intelligent human with any of these four models is more capable than something like Opus 4.7 on its own (see the detailed findings). Please let me know your thoughts! &#32; submitted by &#32; /u/The_Paradoxy [link] &#32; [comments]

</details>