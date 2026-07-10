---
id: inbox_26be7a0c
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/9/muse-spark-1-1/#atom-everything"
author: ""
published_at: 2026-07-09T16:24:09+00:00
fetched_at: 2026-07-09T22:09:43.982211+00:00
content_hash: "c99dff8b9bdc59359e7d3486ee9112003c1f87dc2cd0b6e9cdc92963812e359e"
lang: en
caption_quality: None
raw: true
topics: []
---

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