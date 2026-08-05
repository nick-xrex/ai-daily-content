---
id: inbox_e708d1c6
date: 2026-08-04
source_ref: "[[00-inbox/2026-08-04/0144-simon-willison-llm-anthropic-0-26-d0ca]]"
title: "llm-anthropic 0.26"
url: https://simonwillison.net/2026/Aug/4/llm-anthropic/#atom-everything
source: simon-willison
published_at: 2026-08-04T22:00:58+00:00
fetched_at: 2026-08-05T01:55:18.124241+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llm-anthropic 0.26 發布，為 llm 通用命令列工具帶來重大升級。新增支援三個 Claude 5 系列模型：Fable-5（輕量級）、Sonnet-5（通用）和 Opus-5（旗艦），並整合四個伺服器端工具：WebSearch、WebFetch、CodeExecution 和 AnthropicMCP。新工具均可透過 -T 介面或 Python tools 參數公開存取，取代了先前的 -o web_search* 選項。擴展思考功能重構為 thinking 和 thinking_effort 參數，支援 5 級難度（low、medium、high、xhigh、max），Claude 5 模型預設啟用，Fable-5 始終啟用，Sonnet/Opus 可用 -o thinking 0 禁用。Reasoning 輸出現作為類型化流式事件傳輸，支援 -R/--hide-reasoning 選項隱藏。"
key_points:
  - "新增 Claude Fable-5、Sonnet-5、Opus-5 三款 Claude 5 系列模型支援"
  - "整合伺服器端工具（WebSearch、WebFetch、CodeExecution、AnthropicMCP）透過統一 -T 介面，取代舊有 -o web_search* 參數"
  - "擴展思考簡化為 thinking 和 thinking_effort 參數（5 級：low/medium/high/xhigh/max），Claude 5 預設思考，可逐模型調控"
tags: [llm, anthropic, claude, tool-integration, model-release]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-anthropic 0.26

llm-anthropic 0.26 發布，為 llm 通用命令列工具帶來重大升級。新增支援三個 Claude 5 系列模型：Fable-5（輕量級）、Sonnet-5（通用）和 Opus-5（旗艦），並整合四個伺服器端工具：WebSearch、WebFetch、CodeExecution 和 AnthropicMCP。新工具均可透過 -T 介面或 Python tools 參數公開存取，取代了先前的 -o web_search* 選項。擴展思考功能重構為 thinking 和 thinking_effort 參數，支援 5 級難度（low、medium、high、xhigh、max），Claude 5 模型預設啟用，Fable-5 始終啟用，Sonnet/Opus 可用 -o thinking 0 禁用。Reasoning 輸出現作為類型化流式事件傳輸，支援 -R/--hide-reasoning 選項隱藏。

### 重點
- 新增 Claude Fable-5、Sonnet-5、Opus-5 三款 Claude 5 系列模型支援
- 整合伺服器端工具（WebSearch、WebFetch、CodeExecution、AnthropicMCP）透過統一 -T 介面，取代舊有 -o web_search* 參數
- 擴展思考簡化為 thinking 和 thinking_effort 參數（5 級：low/medium/high/xhigh/max），Claude 5 預設思考，可逐模型調控

**原文：** [simon-willison](https://simonwillison.net/2026/Aug/4/llm-anthropic/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm-anthropic 0.26 
 Includes new features enabled by LLM 0.32 : 
 
 
 New models: claude-fable-5 , claude-sonnet-5 , and claude-opus-5 . #75 , #76 
 Added server-side tools for WebSearch , WebFetch , CodeExecution , and AnthropicMCP , available through LLM's -T interface or Python tools= . The previous -o web_search* options have been removed in favor of -T WebSearch . #79 
 Upgraded to llm&gt;=0.32 . Reasoning, tool calls, tool results, and server-side tool results now stream as typed events. Reasoning for llm CLI prompts now displays to standard error unless you pass --hide-reasoning/-R . 
 Simplified extended thinking to thinking and thinking_effort ( low , medium , high , xhigh , or max ). Claude 5 models think by default; -o thinking 0 disables thinking for Sonnet 5 and Opus 5, while Fable 5 always thinks. -R/--hide-reasoning now omits reasoning from responses and logs. The thinking_budget , thinking_display , and thinking_adaptive options have been removed. #80 
 
 
 
 
 Tags: llm , anthropic , claude , model-context-protocol

</details>