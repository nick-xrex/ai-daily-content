---
id: inbox_750d007c
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tagtpv/i_catalogued_every_way_local_models_break_json/"
author: "/u/kexxty"
published_at: 2026-05-11T21:17:18+00:00
fetched_at: 2026-05-12T01:13:59.593751+00:00
content_hash: "df0bd64f7e46a0d6a03d2361dc8e41ee9382ded77add938cace0acfe8edd7f91"
lang: en
caption_quality: None
raw: true
topics: []
---

# I catalogued every way local models break JSON output and built a repair library, here's what I found across 288 model calls

I've been running structured output prompts through a bunch of models on OpenRouter for the past few months — Llama 3, Mistral, Command R, DeepSeek, Qwen, and every other model on OpenRouter — alongside the usual closed-source suspects. 288 calls total. I wanted to know what actually breaks, how often, and whether open models fail differently from the API-only ones. Short answer: not really. The failure modes are almost identical across the board. The rate varies — some models hit you with markdown fences on nearly every call, others only when you phrase the prompt a certain way; but the categories of breakage are the same everywhere. What I saw most, roughly in order: Markdown fences wrapping the JSON (the model thinks it's being helpful) Trailing commas (JS habits from training data) Python True / False / None instead of JSON true / false / null Truncated objects from running out of tokens mid-response Unescaped quotes inside string values // or # comments inside JSON Literal ... where the model got lazy and didn't generate all the data The reason I'm posting here specifically: most of the advice I see for handling this is &quot;just use JSON mode&quot; or &quot;use a constrained grammar.&quot; And yeah, those help when they're available. But a lot of what people run locally doesn't have reliable JSON mode, grammar-based generation has its own tradeoffs (speed, compatibility), and even when you do get syntactically valid JSON you can still get schema violations and truncation. I ended up building a Python library ( outputguard ) that validates against JSON Schema and runs 15 repair strategies in a specific order when things break. The ordering part turned out to be more important than I expected: fixing encoding before structure, and re-parsing between each strategy so later fixes don't undo earlier ones. Also handles YAML, TOML, and Python literals, which came up more than I thought it would once I started working with models that don't have a JSON mode and just output whatever format they feel like. Wrote up the full findings in a blog post if anyone wants the details: What Breaks When You Ask an LLM for JSON 2,001 tests, MIT licensed, no LLM provider dependencies. pip install outputguard Curious what other people's experience has been — are you seeing the same failure patterns, or are there models/quants that behave differently than what I'm describing? &#32; submitted by &#32; /u/kexxty [link] &#32; [comments]