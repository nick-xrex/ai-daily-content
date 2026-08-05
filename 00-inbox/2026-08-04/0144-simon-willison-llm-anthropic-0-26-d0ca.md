---
id: inbox_e708d1c6
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Aug/4/llm-anthropic/#atom-everything"
author: ""
published_at: 2026-08-04T22:00:58+00:00
fetched_at: 2026-08-05T01:44:31.958166+00:00
content_hash: "d0cae65637bb0192a7161fc3d8fca42b7a6427937ac082fd09c33348383d8e6c"
lang: en
caption_quality: None
raw: true
topics: []
---

# llm-anthropic 0.26

Release: llm-anthropic 0.26 
 Includes new features enabled by LLM 0.32 : 
 
 
 New models: claude-fable-5 , claude-sonnet-5 , and claude-opus-5 . #75 , #76 
 Added server-side tools for WebSearch , WebFetch , CodeExecution , and AnthropicMCP , available through LLM's -T interface or Python tools= . The previous -o web_search* options have been removed in favor of -T WebSearch . #79 
 Upgraded to llm&gt;=0.32 . Reasoning, tool calls, tool results, and server-side tool results now stream as typed events. Reasoning for llm CLI prompts now displays to standard error unless you pass --hide-reasoning/-R . 
 Simplified extended thinking to thinking and thinking_effort ( low , medium , high , xhigh , or max ). Claude 5 models think by default; -o thinking 0 disables thinking for Sonnet 5 and Opus 5, while Fable 5 always thinks. -R/--hide-reasoning now omits reasoning from responses and logs. The thinking_budget , thinking_display , and thinking_adaptive options have been removed. #80 
 
 
 
 
 Tags: llm , anthropic , claude , model-context-protocol