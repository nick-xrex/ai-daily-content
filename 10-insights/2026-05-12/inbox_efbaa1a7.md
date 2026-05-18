---
id: inbox_efbaa1a7
date: 2026-05-12
source_ref: "[[00-inbox/.../inbox_efbaa1a7]]"
title: "llm 0.32a2"
url: https://simonwillison.net/2026/May/12/llm/#atom-everything
source: simon-willison
published_at: 2026-05-12T17:45:07+00:00
fetched_at: 2026-05-18T03:30:56.385797+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LLM 工具發佈 0.32a2 版本，最重要的更新是支持 OpenAI 最新的 /v1/responses 端點（替代 /v1/chat/completions），此端點使 GPT-5 class 模型能執行 interleaved reasoning（在工具呼叫間插入推理步驟）。使用者現在可在命令行看到摘要化的推理 token，並以不同顏色顯示以區別於標準錯誤。新增 -R 或 --hide-reasoning 標誌供不想看推理過程的使用者使用。"
key_points:
  - "OpenAI 模型從 /v1/chat/completions 遷移至 /v1/responses 端點，支持 GPT-5 class 的 interleaved reasoning"
  - "推理 token 現可見且以不同顏色顯示，-R/--hide-reasoning 標誌可隱藏推理詳情"
  - "細粒度推理可視化助於理解模型思考過程，支持更透明的 AI 應用開發"
tags: [llm, openai, gpt-5, reasoning, api-endpoint]
topics: [foundation_models.gpt]
importance: 3
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## llm 0.32a2

LLM 工具發佈 0.32a2 版本，最重要的更新是支持 OpenAI 最新的 /v1/responses 端點（替代 /v1/chat/completions），此端點使 GPT-5 class 模型能執行 interleaved reasoning（在工具呼叫間插入推理步驟）。使用者現在可在命令行看到摘要化的推理 token，並以不同顏色顯示以區別於標準錯誤。新增 -R 或 --hide-reasoning 標誌供不想看推理過程的使用者使用。

### 重點
- OpenAI 模型從 /v1/chat/completions 遷移至 /v1/responses 端點，支持 GPT-5 class 的 interleaved reasoning
- 推理 token 現可見且以不同顏色顯示，-R/--hide-reasoning 標誌可隱藏推理詳情
- 細粒度推理可視化助於理解模型思考過程，支持更透明的 AI 應用開發

**原文：** [simon-willison](https://simonwillison.net/2026/May/12/llm/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# llm 0.32a2

Release: llm 0.32a2 
 A bunch of useful stuff in this LLM alpha, but the most important detail is this one: 
 
 Most reasoning-capable OpenAI models now use the /v1/responses endpoint instead of /v1/chat/completions . This enables interleaved reasoning across tool calls for GPT-5 class models. #1435 
 
 This means you can now see the summarized reasoning tokens when you run prompts against an OpenAI model, displayed in a different color to standard error. Use the -R or --hide-reasoning flags if you don't want to see that. 
 
 
 Tags: llm , projects , openai , generative-ai , annotated-release-notes , ai , llms

</details>