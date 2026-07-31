---
id: inbox_628c85a4
date: 2026-07-30
source_ref: "[[00-inbox/2026-07-30/0107-simon-willison-llm-chat-completions-server-0-1a0-7e6f]]"
title: "llm-chat-completions-server 0.1a0"
url: https://simonwillison.net/2026/Jul/30/llm-chat-completions-server/#atom-everything
source: simon-willison
published_at: 2026-07-30T15:43:16+00:00
fetched_at: 2026-07-31T01:12:40.849260+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 发布了 llm-chat-completions-server v0.1a0 plugin，为 LLM 工具增加了 OpenAI Chat Completions API 兼容的服务器功能。这个 plugin 利用 LLM 0.32rc1 中新的内容可寻址日志（content-addressable logs）设计。通过对消息部分的哈希进行重复数据删除，支持扩展式对话，其中客户端跟踪会话状态，每次请求都包含完整的对话历史。启动后在本地主机的 9001 端口暴露用户已安装的所有 LLM 模型作为 ChatGPT 兼容端点。整个 plugin 由 GPT-5.6 Sol 编写，表明该模型在 OpenAI API 规范和复杂架构设计中的能力。"
key_points:
  - "Plugin 基于 LLM 0.32rc1 的内容可寻址日志设计，通过消息哈希实现数据重复删除和对话树表示"
  - "支持 OpenAI Chat Completions 风格的扩展式对话，本地 9001 端口暴露所有已安装模型作为 ChatGPT 兼容端点"
  - "整个 plugin 由 GPT-5.6 Sol 自动生成，演示了该模型对复杂 API 规范和架构设计的掌握"
tags: [llm, openai-api, plugin, chat-completions]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-chat-completions-server 0.1a0

Simon Willison 发布了 llm-chat-completions-server v0.1a0 plugin，为 LLM 工具增加了 OpenAI Chat Completions API 兼容的服务器功能。这个 plugin 利用 LLM 0.32rc1 中新的内容可寻址日志（content-addressable logs）设计。通过对消息部分的哈希进行重复数据删除，支持扩展式对话，其中客户端跟踪会话状态，每次请求都包含完整的对话历史。启动后在本地主机的 9001 端口暴露用户已安装的所有 LLM 模型作为 ChatGPT 兼容端点。整个 plugin 由 GPT-5.6 Sol 编写，表明该模型在 OpenAI API 规范和复杂架构设计中的能力。

### 重點
- Plugin 基于 LLM 0.32rc1 的内容可寻址日志设计，通过消息哈希实现数据重复删除和对话树表示
- 支持 OpenAI Chat Completions 风格的扩展式对话，本地 9001 端口暴露所有已安装模型作为 ChatGPT 兼容端点
- 整个 plugin 由 GPT-5.6 Sol 自动生成，演示了该模型对复杂 API 规范和架构设计的掌握

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/30/llm-chat-completions-server/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm-chat-completions-server 0.1a0 
 A key goal of the new content-addressable logs in LLM 0.32rc1 was being able to support OpenAI Chat Completion style requests where each incoming message extends the previous conversation, like this: 
 curl http://localhost:8002/v1/chat/completions \
 -H 'Content-Type: application/json' \
 -d '{
 "model": "qwen3.5-4b",
 "messages": [
 {"role": "user", "content": "Capital of France?"},
 {"role": "assistant", "content": "Paris."},
 {"role": "user", "content": "Germany?"}
 ]
 }'
 
 Here the conversation state is tracked by the client, so each of these requests gets longer and longer. The new schema design in LLM is designed to de-duplicate these using hashes of the individual message parts. 
 To test that out, I built this plugin: 
 uv tool install llm --pre
llm install llm-chat-completions-server
llm chat-completions-server -p 9001
 
 Running this starts a localhost server on port 9001 that exposes your full collection of LLM models (from any plugins you have installed) using a ChatGPT Completions compatible endpoint. 
 GPT-5.6 Sol wrote the whole thing - it turns out it knows the OpenAI Chat Completions API shape really well. 
 
 
 Tags: projects , openai , llm

</details>