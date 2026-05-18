---
id: inbox_1c0ad7bb
source: hackernews
source_type: hn
url: "https://github.com/cactus-compute/needle"
author: "HenryNdubuaku"
published_at: 2026-05-12T18:03:11+00:00
fetched_at: 2026-05-18T03:09:28.107837+00:00
content_hash: "62721348bf122fa2e9675f39fd24d8d30124d9793bdb7c13323e297d6c0c868d"
lang: en
caption_quality: None
raw: true
topics: []
---

# Show HN: Needle: We Distilled Gemini Tool Calling into a 26M Model

Hey HN, Henry here from Cactus. We open-sourced Needle, a 26M parameter function-calling (tool use) model. It runs at 6000 tok&#x2F;s prefill and 1200 tok&#x2F;s decode on consumer devices. We were always frustrated by the little effort made towards building agentic models that run on budget phones, so we conducted investigations that led to an observation: agentic experiences are built upon tool calling, and massive models are overkill for it. Tool calling is fundamentally retrieval-and-assembly (match query to tool name, extract argument values, emit JSON), not reasoning. Cross-attention is the right primitive for this, and FFN parameters are wasted at this scale. Simple Attention Networks: the entire model is just attention and gating, no MLPs anywhere. Needle is an experimental run for single-shot function calling for consumer devices (phones, watches, glasses...). Training:
- Pretrained on 200B tokens across 16 TPU v6e (27 hours)
- Post-trained on 2B tokens of synthesized function-calling data (45 minutes)
- Dataset synthesized via Gemini with 15 tool categories (timers, messaging, navigation, smart home, etc.) You can test it right now and finetune on your Mac&#x2F;PC: https:&#x2F;&#x2F;github.com&#x2F;cactus-compute&#x2F;needle The full writeup on the architecture is here: https:&#x2F;&#x2F;github.com&#x2F;cactus-compute&#x2F;needle&#x2F;blob&#x2F;main&#x2F;docs&#x2F;simp... We found that the &quot;no FFN&quot; finding generalizes beyond function calling to any task where the model has access to external structured knowledge (RAG, tool use, retrieval-augmented generation). The model doesn&#x27;t need to memorize facts in FFN weights if the facts are provided in the input. Experimental results to published. While it beats FunctionGemma-270M, Qwen-0.6B, Granite-350M, LFM2.5-350M on single-shot function calling, those models have more scope&#x2F;capacity and excel in conversational settings. We encourage you to test on your own tools via the playground and finetune accordingly. This is part of our broader work on Cactus ( https:&#x2F;&#x2F;github.com&#x2F;cactus-compute&#x2F;cactus ), an inference engine built from scratch for mobile, wearables and custom hardware. We wrote about Cactus here previously: https:&#x2F;&#x2F;news.ycombinator.com&#x2F;item?id=44524544 Everything is MIT licensed. Weights: https:&#x2F;&#x2F;huggingface.co&#x2F;Cactus-Compute&#x2F;needle 
GitHub: https:&#x2F;&#x2F;github.com&#x2F;cactus-compute&#x2F;needle