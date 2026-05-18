---
id: inbox_efbaa1a7
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/May/12/llm/#atom-everything"
author: ""
published_at: 2026-05-12T17:45:07+00:00
fetched_at: 2026-05-14T18:18:06.571535+00:00
content_hash: "b358b42417629a51d09d646acc25203e8e322d832e92fb8f3813893f3fd29199"
lang: en
caption_quality: None
raw: true
topics: []
---

# llm 0.32a2

Release: llm 0.32a2 
 A bunch of useful stuff in this LLM alpha, but the most important detail is this one: 
 
 Most reasoning-capable OpenAI models now use the /v1/responses endpoint instead of /v1/chat/completions . This enables interleaved reasoning across tool calls for GPT-5 class models. #1435 
 
 This means you can now see the summarized reasoning tokens when you run prompts against an OpenAI model, displayed in a different color to standard error. Use the -R or --hide-reasoning flags if you don't want to see that. 
 
 
 Tags: llm , projects , openai , generative-ai , annotated-release-notes , ai , llms