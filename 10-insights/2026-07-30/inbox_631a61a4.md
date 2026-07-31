---
id: inbox_631a61a4
date: 2026-07-30
source_ref: "[[00-inbox/2026-07-30/0107-simon-willison-llm-0-32rc2-f7e1]]"
title: "llm 0.32rc2"
url: https://simonwillison.net/2026/Jul/30/llm-rc2/#atom-everything
source: simon-willison
published_at: 2026-07-30T22:52:06+00:00
fetched_at: 2026-07-31T01:12:40.843391+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 发布了 LLM CLI 工具的 0.32rc2 版本，修复了依赖问题并添加了两项新功能。首先，默认模型从 GPT-4o mini ($0.15/$0.60) 改为 GPT-5.6 Luna ($0.20/M input、$1.20/M output)。用户可通过 `llm models default` 命令切换回 4o mini 或更便宜的 GPT-5 nano ($0.05/$0.40)。其次新增 `llm openai endpoint` 命令，允许针对任意 OpenAI 兼容端点运行 prompts、chats 和 model listings，无需预先配置模型。这些调用不被记录在 LLM 的日志中。该命令支持本地模型（如通过 uvx 一行命令调用 LM Studio 的 Gemma-4-31b），为开发者提供了快速试验各类端点的便利。"
key_points:
  - "新增 `llm openai endpoint` 命令支持任意 OpenAI 兼容端点，无需预配置，调用不记录在日志中（PR #1565）"
  - "默认模型从 GPT-4o mini 切换至 GPT-5.6 Luna，用户可用 `llm models default gpt-4o-mini` 或 `llm models default gpt-5-nano` 自由选择（PR #1576）"
  - "支持通过 uvx 单行命令快速测试本地或远程 OpenAI 兼容模型，如 `uvx --pre llm openai endpoint http://127.0.0.1:1234/v1`"
tags: [llm, cli-tool, openai-compatibility, model-default]
topics: []
importance: 2
novelty: 3
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## llm 0.32rc2

Simon Willison 发布了 LLM CLI 工具的 0.32rc2 版本，修复了依赖问题并添加了两项新功能。首先，默认模型从 GPT-4o mini ($0.15/$0.60) 改为 GPT-5.6 Luna ($0.20/M input、$1.20/M output)。用户可通过 `llm models default` 命令切换回 4o mini 或更便宜的 GPT-5 nano ($0.05/$0.40)。其次新增 `llm openai endpoint` 命令，允许针对任意 OpenAI 兼容端点运行 prompts、chats 和 model listings，无需预先配置模型。这些调用不被记录在 LLM 的日志中。该命令支持本地模型（如通过 uvx 一行命令调用 LM Studio 的 Gemma-4-31b），为开发者提供了快速试验各类端点的便利。

### 重點
- 新增 `llm openai endpoint` 命令支持任意 OpenAI 兼容端点，无需预配置，调用不记录在日志中（PR #1565）
- 默认模型从 GPT-4o mini 切换至 GPT-5.6 Luna，用户可用 `llm models default gpt-4o-mini` 或 `llm models default gpt-5-nano` 自由选择（PR #1576）
- 支持通过 uvx 单行命令快速测试本地或远程 OpenAI 兼容模型，如 `uvx --pre llm openai endpoint http://127.0.0.1:1234/v1`

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/30/llm-rc2/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm 0.32rc2 
 Hot on the heels of RC1 , this fixes a dependency issue and also adds two neat new features: 
 
 
 The default model for users who have not set their own default is now GPT-5.6 Luna . It was previously GPT-4o mini . Luna is a much better and more recent model, albeit slightly more expensive - $0.20 per million input tokens and $1.20 per million output tokens, compared to $0.15/$0.60 for 4o mini. You can switch back to 4o mini using llm models default gpt-4o-mini , or switch to GPT-5 nano , an even cheaper default model ($0.05/$0.40), using llm models default gpt-5-nano . #1576 
 New llm openai endpoint command for running prompts, chats and model listings against arbitrary OpenAI-compatible endpoints without first configuring a model. These calls are not logged. #1565 
 
 
 The llm openai endpoint command is really cool. I got frustrated at the lack of an obvious CLI tool for trying out prompts against arbitrary OpenAI Chat Completions imitation endpoints, so I decided to add that to LLM itself. 
 You don't even have to install LLM to use this. Here's a uvx one-liner for running a prompt - with tools - against an LM Studio local model: 
 uvx --pre llm openai endpoint http://127.0.0.1:1234/v1 \
 T llm_version -T llm_time --td \
 -m google/gemma-4-31b 'what is the current LLM version? And the time?'
 
 Output here . 
 
 
 Tags: llm , uv , lm-studio

</details>