---
id: inbox_d4a06a46
date: 2026-07-08
source_ref: "[[00-inbox/.../inbox_d4a06a46]]"
title: "Introducing GPT‐Live"
url: https://simonwillison.net/2026/Jul/8/introducing-gptlive/#atom-everything
source: simon-willison
published_at: 2026-07-08T23:20:48+00:00
fetched_at: 2026-07-10T00:48:24.707249+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 升級 ChatGPT voice mode 使用的模型，推出稱 GPT-Live 的新實現。GPT-Live 能將需要網路搜尋、深度推理或複雜計算的任務委派給背景的 GPT-5.5 模型處理，同時保持與用戶的語音對話流暢。前一代 voice mode 基於 GPT-4o era 舊模型，知識截止約 2024 年。Simon Willison 預覽期間發現模型會不恰當打斷用戶笑話（已修正），並完成最長一小時的連續語音對話。"
key_points:
  - "GPT-Live 支援動態任務委派至背景 GPT-5.5（web search、深度推理、複雜計算），保持對話流暢無感知延遲"
  - "知識截止與模型版本大幅推進，從 GPT-4o era (2024) → GPT-5.5 era，可信度與實用性提升"
  - "OpenAI 承諾隨新 frontier models 發布持續更新 GPT-Live 背景模型"
tags: [openai, gpt-live, gpt-5.5, voice-mode, multi-model-delegation]
topics: [foundation_models.gpt]
importance: 4
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Introducing GPT‐Live

OpenAI 升級 ChatGPT voice mode 使用的模型，推出稱 GPT-Live 的新實現。GPT-Live 能將需要網路搜尋、深度推理或複雜計算的任務委派給背景的 GPT-5.5 模型處理，同時保持與用戶的語音對話流暢。前一代 voice mode 基於 GPT-4o era 舊模型，知識截止約 2024 年。Simon Willison 預覽期間發現模型會不恰當打斷用戶笑話（已修正），並完成最長一小時的連續語音對話。

### 重點
- GPT-Live 支援動態任務委派至背景 GPT-5.5（web search、深度推理、複雜計算），保持對話流暢無感知延遲
- 知識截止與模型版本大幅推進，從 GPT-4o era (2024) → GPT-5.5 era，可信度與實用性提升
- OpenAI 承諾隨新 frontier models 發布持續更新 GPT-Live 背景模型

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/8/introducing-gptlive/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Introducing GPT‐Live

Introducing GPT‐Live 
OpenAI finally upgraded the model used by ChatGPT voice mode! 
 I've had preview access for a few weeks in the iPhone app, and the new model is very impressive. It also has the ability to spin off harder tasks to GPT-5.5: 
 
 For questions that require web search, deeper reasoning, or more complex work, it delegates to our latest frontier model behind the scenes and brings the result back into the conversation when it’s ready. While it works, GPT‐Live can keep talking with you and maintain the flow of conversation. At launch, GPT‐Live will use GPT‐5.5 in the background. As we release new frontier models, we’ll continuously update the model used by GPT‐Live. 
 
 The previous voice mode in the ChatGPT app was based on a GPT-4o era model, with a knowledge cut-off some time in 2024. I had mostly stopped using voice mode because the age and relative weakness of the model greatly limited how useful it was as a brainstorming partner. 
 During the preview period I encountered a pretty obscure bug: the model was interrupting me to laugh at things I said, which weren't even intended as jokes! It felt rude and condescending - I reported it to OpenAI and as far as I can tell they made some tweaks and it's now less likely to happen. 
 From looking back at my transcripts I think it was this bit that triggered the interrupting laugh: 
 
 so where are the owls when they're not, like before dusk? The owls exist, right? Are they hiding in holes? Where are they hiding? 
 
 My longest conversation with the new model has been a full hour while walking the dog (and taking photos of pelicans ). I have not yet managed to take a photo of an owl.

 Via Hacker News 

 Tags: text-to-speech , ai , openai , generative-ai , llms , multi-modal-output , llm-release , speech-to-text

</details>