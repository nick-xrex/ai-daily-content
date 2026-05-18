---
id: inbox_a6d4361b
date: 2026-05-17
source_ref: "[[00-inbox/.../inbox_a6d4361b]]"
title: "Deepseek V4&#39;s 1M context window: the breaking point"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tfhl0q/deepseek_v4s_1m_context_window_the_breaking_point/
source: reddit-localllama
published_at: 2026-05-17T06:35:44+00:00
fetched_at: 2026-05-18T04:10:16.965419+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "實測 Deepseek V4 在三個真實代碼庫（45k、180k、520k tokens）上的精度衰減曲線。結論：150–250k token 是最佳工作範圍（<2s TTFT、完整 context 保留），300k+ 開始質量下降，400k+ 精確度明顯衰退（誤差 ±行號，如 247 變「around 230」），520k 淪為架構摘要。同時測得 94% hallucination rate on unknown-answer tasks。建議：雖號稱 1M，實務上限制在 250k 以內，或接受額外驗證成本。"
key_points:
  - "實測最佳範圍 150–250k tokens：完整 context 保留、<2s TTFT、最小精度損失；multi-file refactor 跨 14 檔無矛盾"
  - "精度衰減曲線：300k 質量開始下滑，400k+ 行號誤差 ±17（247 → ~230），520k 變成架構摘要、跳過實現細節"
  - "94% hallucination rate on unknown-answer tasks；Max reasoning mode TTFT ~120s，影響互動工作流，需防禦性提示及源碼驗證"
tags: [deepseek-v4, context-window, precision-degradation, hallucination-rate]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Deepseek V4's 1M context window: the breaking point

實測 Deepseek V4 在三個真實代碼庫（45k、180k、520k tokens）上的精度衰減曲線。結論：150–250k token 是最佳工作範圍（<2s TTFT、完整 context 保留），300k+ 開始質量下降，400k+ 精確度明顯衰退（誤差 ±行號，如 247 變「around 230」），520k 淪為架構摘要。同時測得 94% hallucination rate on unknown-answer tasks。建議：雖號稱 1M，實務上限制在 250k 以內，或接受額外驗證成本。

### 重點
- 實測最佳範圍 150–250k tokens：完整 context 保留、<2s TTFT、最小精度損失；multi-file refactor 跨 14 檔無矛盾
- 精度衰減曲線：300k 質量開始下滑，400k+ 行號誤差 ±17（247 → ~230），520k 變成架構摘要、跳過實現細節
- 94% hallucination rate on unknown-answer tasks；Max reasoning mode TTFT ~120s，影響互動工作流，需防禦性提示及源碼驗證

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tfhl0q/deepseek_v4s_1m_context_window_the_breaking_point/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Deepseek V4's 1M context window: the breaking point

Just ran to verify deepseek v4's context claim of 1M and ran it across three production codebases like 45k (microservice), 180k (monorepo backend) and 520k(full stack app). For the observation, tasks included dependency tracing, cross file refractors and bug isolation to see where recall keeps up under 150k Got a solid performance like at 45k tokens, function calls traced across 8 files maintain accurate path reconstruction. At 180k, multi file refractors spanning 14 files show consistent architectural understand and no contradictions or context loss patterns past 300k precision quality degrades here. asked for exact line numbers from functions defined 400k tokens earlier, responses give &quot;around line 230&quot; instead of the actual 247. at 520k outputs shift to architectural summaries that skip implementation details, thats a problem if edge cases are a concern the latency gap Time to first token measures around 1.19s on deepinfra fp4 endpoint. Time to first answer in max reasoning mode stretches to around 120 seconds since the model completes internal chain of thought before producing visible output, which is really crticial for interative workflows to account for provider benchmarks show 94% hallucination rate on unknown asnwer tasks (aa-omniscience) but v4 generates confident responses without even actual info. Shows up as references to nonexistent utility functions or phantom dependencies on unknown answer tasks v4 generates confident responses without actual grounding, shows up as references to nonexistent utility functions or phantom dependencies. needs a validation layer for anything production critical practical range 150-250k tokens appears optimal for coding work. full context retention, sub 2s response latency, minimal precision loss. past 300k requires defensive prompting and source verification. the 1m window functions technically but needs careful handling tho. context size shifts which prompt engineering techniques matter rather than eliminating the need completely &#32; submitted by &#32; /u/TangeloOk9486 [link] &#32; [comments]

</details>