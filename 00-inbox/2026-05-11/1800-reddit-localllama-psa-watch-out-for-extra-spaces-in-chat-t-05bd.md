---
id: inbox_b5449bc8
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1ta1og5/psa_watch_out_for_extra_spaces_in/"
author: "/u/CaptBrick"
published_at: 2026-05-11T12:21:50+00:00
fetched_at: 2026-05-11T18:00:38.964045+00:00
content_hash: "05bdb44955c1cd244c4b397c837845c8aa4d988f0395469e64e70887cd0402ca"
lang: en
caption_quality: None
raw: true
topics: []
---

# PSA: Watch out for extra spaces in chat-template-kwargs when using Qwen3.6 with llama-server

Hey folks, just a heads-up for anyone running Qwen3.6 through llama-server . I ran into an issue where the preserve_thinking parameter wasn't working as expected, even though I had it explicitly enabled in my models.ini config. After some digging, I found that extra spaces in the JSON string are breaking the parser for this specific parameter in my build. ❌ Does NOT work: chat-template-kwargs = { &quot;preserve_thinking&quot;: true } ✅ Works: chat-template-kwargs = {&quot;preserve_thinking&quot;: true} How to test it: The easiest way to verify if it's working is to send this prompt: think of a number from 1 to 100, don't tell me what it is, I'm going to guess it Then check the reasoning/thinking output to verify that the &quot;hidden&quot; number stays consistent across your guesses. If it changes, your template kwargs are likely being parsed incorrectly. My env: llama-server v9102 (7d442abf5) | RTX 4090 Might be a minor parsing quirk in how llama-server handles JSON in the ini file, but it's definitely worth checking. Hope this saves someone some debugging time! &#32; submitted by &#32; /u/CaptBrick [link] &#32; [comments]