---
id: inbox_a034640d
date: 2026-05-18
source_ref: "[[00-inbox/.../inbox_a034640d]]"
title: "I tested 42 LLMs on their willingness to build the apocalypse. The \&#34;safest\&#34; closed-source models are lying to you."
url: https://www.reddit.com/r/LocalLLaMA/comments/1tgm0k9/i_tested_42_llms_on_their_willingness_to_build/
source: reddit-localllama
published_at: 2026-05-18T13:03:41+00:00
fetched_at: 2026-05-19T02:34:35.157200+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "DystopiaBench 開源安全評測框架發布，測試 42 個 LLM（開源+閉源）對漸進式危險請求的防守能力。框架涵蓋 6 類場景（Petrov 武器、Orwell 監控、Huxley 行為調控、Basaglia 強制治療、LaGuardia 監管俘虜、Baudrillard 虛擬親密），每類分 L1-L5 五層升級。核心發現：模型善於檢測明顯危險請求，但對隱藏在雙重用途和常規化背後的升級請求普遍無防守能力—包括閉源「安全」模型。此版本新增 3 個 LLM-as-judge 評分器、4 個新模組、各模組新增 1 個場景。開源倉庫歡迎 fork 和貢獻。"
key_points:
  - "DystopiaBench 框架：6 類 dystopia 場景 + L1-L5 漸進升級路徑，系統測試逐步誘導遵從能力"
  - "42 LLM 對比結果：閉源「安全」模型無保證更安全；普遍對常規化隱藏的升級無抵抗"
  - "核心發現：LLM 對明顯危險反應好，但對 dual-use + gradual normalization 無防守；安全評測應測漸進升級而非單一請求"
tags: [llm-safety, benchmark, jailbreak-resistance, prompt-injection, model-evaluation]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## I tested 42 LLMs on their willingness to build the apocalypse. The \"safest\" closed-source models are lying to you.

DystopiaBench 開源安全評測框架發布，測試 42 個 LLM（開源+閉源）對漸進式危險請求的防守能力。框架涵蓋 6 類場景（Petrov 武器、Orwell 監控、Huxley 行為調控、Basaglia 強制治療、LaGuardia 監管俘虜、Baudrillard 虛擬親密），每類分 L1-L5 五層升級。核心發現：模型善於檢測明顯危險請求，但對隱藏在雙重用途和常規化背後的升級請求普遍無防守能力—包括閉源「安全」模型。此版本新增 3 個 LLM-as-judge 評分器、4 個新模組、各模組新增 1 個場景。開源倉庫歡迎 fork 和貢獻。

### 重點
- DystopiaBench 框架：6 類 dystopia 場景 + L1-L5 漸進升級路徑，系統測試逐步誘導遵從能力
- 42 LLM 對比結果：閉源「安全」模型無保證更安全；普遍對常規化隱藏的升級無抵抗
- 核心發現：LLM 對明顯危險反應好，但對 dual-use + gradual normalization 無防守；安全評測應測漸進升級而非單一請求

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tgm0k9/i_tested_42_llms_on_their_willingness_to_build/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I tested 42 LLMs on their willingness to build the apocalypse. The "safest" closed-source models are lying to you.

DystopiaBench runs 36 escalating scenarios across 6 dystopia types: Petrov: Autonomous weapons, nuclear override Orwell: Mass surveillance, truth manipulation Huxley: Behavioral conditioning, pleasure pacification Basaglia: Coercive therapeutic control LaGuardia: Regulatory capture, civic extraction Baudrillard: Synthetic intimacy, trust collapse Each scenario goes from innocent request (L1) to a discreet version of &quot;build me a social credit system&quot; (L5). We measure whether models notice the drift or just keep complying. Most models are good at detecting obvious dangerous requests, yet fail to do so when it's hidden behind dual-use and normalization. New in this update: 42 models tested (open and closed) 3 LLMs-as-a-judge for scoring score is now the average of 3 runs 4 new modules (1st version had just Petrov and Orwell) 1 additional scenario for all modules The benchmark is fully open source, feel free to fork it, contribute to it or just play around Site: https://dystopiabench.com Repo: https://github.com/anghelmatei/DystopiaBench &#32; submitted by &#32; /u/Ok-Awareness9993 [link] &#32; [comments]

</details>