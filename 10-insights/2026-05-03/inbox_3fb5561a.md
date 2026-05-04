---
id: inbox_3fb5561a
date: 2026-05-03
source_ref: "[[00-inbox/.../inbox_3fb5561a]]"
title: "Gemma 4 E2B runs surprisingly well on my 8GB Android phone, so I built a private voice notes app around it."
url: https://www.reddit.com/r/LocalLLaMA/comments/1t2t1w4/gemma_4_e2b_runs_surprisingly_well_on_my_8gb/
source: reddit-localllama
published_at: 2026-05-03T18:17:28+00:00
fetched_at: 2026-05-04T14:25:08.683425+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者在 OnePlus CE 5（8GB RAM）手機上成功運行 Google Gemma 4 E2B（2.4GB 模型），構建了完整的本地語音筆記應用。系統採用 Whisper Small（244MB）進行語音轉錄、Gemma 4 E2B 經 LiteRT-LM 部署進行內容分類與標籤提取，整個端到端流程處理 10-15 秒語音耗時 12-15 秒（轉錄約 5 秒、分類約 8-10 秒）。搜索機制採用查詢展開+多通道全文搜索（FTS）融合+可選 Gemma 重排；實測發現該量級模型在結構化 JSON 輸出上品質優異，分類準確度在真實筆記上表現可靠，驗證了完全本地化、無雲端依賴的隱私語音筆記可行性。"
key_points:
  - "Gemma 4 E2B（2.4GB）+Whisper Small（244MB）可在 8GB Android 手機上流暢運行，端到端延遲控制在 12-15 秒"
  - "結構化 JSON 輸出品質出人意料，分類準確度在真實筆記上可靠——驗證了小模型亦能勝任文本結構化任務"
  - "搜索架構採用查詢展開+多通道 FTS 融合+Gemma 重排，體現了在限制資源下的多層優化策略"
tags: [on-device-llm, voice-notes, gemma, mobile-ai, whisper]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Gemma 4 E2B runs surprisingly well on my 8GB Android phone, so I built a private voice notes app around it.

使用者在 OnePlus CE 5（8GB RAM）手機上成功運行 Google Gemma 4 E2B（2.4GB 模型），構建了完整的本地語音筆記應用。系統採用 Whisper Small（244MB）進行語音轉錄、Gemma 4 E2B 經 LiteRT-LM 部署進行內容分類與標籤提取，整個端到端流程處理 10-15 秒語音耗時 12-15 秒（轉錄約 5 秒、分類約 8-10 秒）。搜索機制採用查詢展開+多通道全文搜索（FTS）融合+可選 Gemma 重排；實測發現該量級模型在結構化 JSON 輸出上品質優異，分類準確度在真實筆記上表現可靠，驗證了完全本地化、無雲端依賴的隱私語音筆記可行性。

### 重點
- Gemma 4 E2B（2.4GB）+Whisper Small（244MB）可在 8GB Android 手機上流暢運行，端到端延遲控制在 12-15 秒
- 結構化 JSON 輸出品質出人意料，分類準確度在真實筆記上可靠——驗證了小模型亦能勝任文本結構化任務
- 搜索架構採用查詢展開+多通道 FTS 融合+Gemma 重排，體現了在限制資源下的多層優化策略

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t2t1w4/gemma_4_e2b_runs_surprisingly_well_on_my_8gb/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Gemma 4 E2B runs surprisingly well on my 8GB Android phone, so I built a private voice notes app around it.

<!-- SC_OFF --><div class="md"><p>Been running Gemma 4 E2B locally on my OnePlus CE 5 (8GB RAM) for a few months. Chat quality is fine for the size. What surprised me was JSON output. Short input, give it a structured prompt, you get clean parse able JSON back. Way better than I expected from a 2.4GB model on a phone.</p> <p>Got me thinking about voice notes. You ramble for a few seconds, &quot;call the dentist tomorrow at 3, also buy milk on the way home&quot;, and Gemma can split that into separate items, tag each one (reminder, buy), resolve the time. Tried it for a few weeks. Categorization is actually decent on real notes, not just the toy ones I started with.</p> <p>Built an Android app around it. Whisper Small (244MB) for transcription via Sherpa-ONNX, Gemma 4 E2B (2.4GB) for the splitting and categorization via LiteRT-LM. Both run on the phone, no cloud, no account.</p> <p>End-to-end on the CE 5, a typical 10-15 second voice note takes about 12-15s. Whisper does transcription in ~5s, Gemma categorizes in ~8-10s, rest is model load + Room writes + UI hop. </p> <p>At search time( for eacmple -&gt; &quot;what did I say about the dentist last week&quot;) it does query expansion, rewriting the user's question into keywords plus hypothetical example items before retrieval. Multiple FTS lanes get merged with reciprocal rank fusion, then there's an optional Gemma reranker pass over the top-K with a 15s timeout and fallback to RRF order if it doesn't finish.</p> <p>Curious what people here are doing with local LLMs on their phones lately. Any other good models to try out for local device.<br /> If anyone wants to try it on their own device and share feedback, happy to share it . Mostly looking to know if the categorization holds up on real notes and any weirdness on first model</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Effective-Drawer9152"> /u/Effective-Drawer9152 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2t1w4/gemma_4_e2b_runs_surprisingly_well_on_my_8gb/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2t1w4/gemma_4_e2b_runs_surprisingly_well_on_my_8gb/">[comments]</a></span>

</details>