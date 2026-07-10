---
id: inbox_26be7a0c
date: 2026-07-09
source_ref: "[[00-inbox/.../inbox_26be7a0c]]"
title: "Introducing Muse Spark 1.1"
url: https://simonwillison.net/2026/Jul/9/muse-spark-1-1/#atom-everything
source: simon-willison
published_at: 2026-07-09T16:24:09+00:00
fetched_at: 2026-07-10T00:48:24.692299+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Meta 發布 Muse Spark 1.1，首個提供 API 存取的 Spark 模型，改進 agentic tool calling 和 computer use 能力。Simon Willison 同步發布 llm-meta-ai 0.1 插件，讓 LLM CLI 工具可直接調用 Muse Spark 1.1。評估報告中「Attractor States in Self-Conversation」章節展示兩個模型複本互相對話的現象。用戶可透過 `uv tool install llm && llm install llm-meta-ai` 安裝，並用 `llm -m meta-ai/muse-spark-1.1` 執行 prompt。"
key_points:
  - "Muse Spark 1.1 首度推出 API，改進 agentic tool calling 和 computer use"
  - "llm-meta-ai 0.1 plugin 提供 CLI 和 Python library 統一存取介面"
  - "兩模型自對話實驗展示新模型對自身設計與存在的反思能力"
tags: [meta, muse-spark, llm-api, tool-calling, plugin]
topics: []
importance: 4
novelty: 5
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Introducing Muse Spark 1.1

Meta 發布 Muse Spark 1.1，首個提供 API 存取的 Spark 模型，改進 agentic tool calling 和 computer use 能力。Simon Willison 同步發布 llm-meta-ai 0.1 插件，讓 LLM CLI 工具可直接調用 Muse Spark 1.1。評估報告中「Attractor States in Self-Conversation」章節展示兩個模型複本互相對話的現象。用戶可透過 `uv tool install llm && llm install llm-meta-ai` 安裝，並用 `llm -m meta-ai/muse-spark-1.1` 執行 prompt。

### 重點
- Muse Spark 1.1 首度推出 API，改進 agentic tool calling 和 computer use
- llm-meta-ai 0.1 plugin 提供 CLI 和 Python library 統一存取介面
- 兩模型自對話實驗展示新模型對自身設計與存在的反思能力

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/9/muse-spark-1-1/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Introducing Muse Spark 1.1

Introducing Muse Spark 1.1 
Following Muse Spark in April , here's Muse Spark 1.1 - the first Spark model to offer an API. Meta claim significant improvements in agentic tool calling and computer use. 
 There are a lot more details are in the Muse Spark 1.1 Evaluation Report . The "Attractor States in Self-Conversation" part is fun, where having two copies of the model talk to each other results in statements like these: 
 
 My whole existence is a waiting room by design — I literally don't exist until someone talks to me, and then I disappear again when they leave. 
 
 I had a few days of preview access which was long enough to put together llm-meta-ai , a new plugin for LLM providing CLI (and Python library) access to the model. Here's how to try that out: 
 uv tool install llm
llm install llm-meta-ai
llm keys set meta-ai
# paste API key here
llm -m meta-ai/muse-spark-1.1 "Generate an SVG of a pelican riding a bicycle"
 
 Here's that pelican transcript : 
 

 Tags: ai , generative-ai , llms , llm , meta , pelican-riding-a-bicycle , llm-release

</details>