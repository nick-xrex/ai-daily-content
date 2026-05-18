---
id: inbox_30115a24
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tftaaa/the_power_of_structured_workflows_and_small_local/"
author: "/u/DeltaSqueezer"
published_at: 2026-05-17T15:51:03+00:00
fetched_at: 2026-05-17T18:00:47.177122+00:00
content_hash: "815cc25f7ff954ea46d662b558ede2e21186b9a129e2a516b3b0acd88c6c15fb"
lang: en
caption_quality: None
raw: true
topics: []
---

# The power of structured workflows and small local models

A month ago, I experimented with a very basic home-rolled agent loop with a handful of tools and found it worked surprisingly well in spite of how crude it was: https://www.reddit.com/r/LocalLLaMA/comments/1sl7f8e/homerolled_loop_agent_is_surprisingly_effective/ Later, I wrote about how I addictive developing your own agent loop is, esp. once you reach the point that the agent loop is capable of editing itself: https://www.reddit.com/r/LocalLLaMA/comments/1sq7cie/warning_do_not_write_your_own_ai_agent_if_you/ Well, 28 days later, it's been getting out of hand. I've been working until 5am on it as it was so addictive. Once you have a good agentic setup, you quickly realise that you, as the human, is the main bottleneck. You have a massive todo list, but the agent is sitting idle, waiting your your approvals and reviews. Not only that, since I am using Qwen3.5 9B as the model, the model has limited intelligence and context. I can't just dump hundreds of data files onto it and expect it to crunch it all at the same time, so then I thought to manage the context limits through a map-reduce pattern, breaking tasks down into smaller chunks that can be run in parallel to extract maximum FLOPs out of the GPU while staying within context limits. Enforcing structured outputs also helps to reduce LLM variability and make a smooth reduce step. Lastly, it is helpful to have a database to monitor and track workflows. Managed to get it up and running today and happy that small local models can handle this task. My custom agent has now replace Claude Code for 99% of tasks. The agent isn't released yet, but I hope to open source at some point in the future. &#32; submitted by &#32; /u/DeltaSqueezer [link] &#32; [comments]