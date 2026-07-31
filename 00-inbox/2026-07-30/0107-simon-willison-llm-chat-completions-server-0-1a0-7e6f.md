---
id: inbox_628c85a4
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/30/llm-chat-completions-server/#atom-everything"
author: ""
published_at: 2026-07-30T15:43:16+00:00
fetched_at: 2026-07-31T01:07:27.817119+00:00
content_hash: "7e6fda787615f296419763441e874922221a8127c150230b4a8e12caf073ef7e"
lang: en
caption_quality: None
raw: true
topics: []
---

# llm-chat-completions-server 0.1a0

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