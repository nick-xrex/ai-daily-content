---
id: inbox_71303bee
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tgkyud/if_you_use_continuedev_and_qwen_36_dense_moe_i/"
author: "/u/Jorlen"
published_at: 2026-05-18T12:21:41+00:00
fetched_at: 2026-05-19T02:01:31.478382+00:00
content_hash: "10c1942a0710c61943215da974b520ee3d518f7153e4e903a4fbbe1f4c14a475"
lang: en
caption_quality: None
raw: true
topics: []
---

# If you use continue.dev and Qwen 3.6 (dense / MoE) - I could use your help

Someone suggested I give Continue (Vscode extension) a try. I've been using Roo / Zoo now and liking it but it is pretty tough on context and I was told continue has more control over it. Anyways, I got it working, at the core... they talk to one another but something strange is happening. I've tried both Qwen 3.6 models; the dense 27b and 35B/A3B. If you ask it simple chats, no problem. But if you then call it to do any coding calls, or file reads, it'll think and then just.. stop. The actual output doesn't come out. I can see the thinking block but not the output. The template is fine, works everywhere else including via Roo and I've played about with the max reasoning budget setting of llama.cpp (docker server version). I know the reasoning budget settings works because if I drop into llama's own interface and ask it to describe quantum mechanics, it abruptly halts the thinking process at exactly the same token use amount (watching it stop Qwen at 1024 has been amusing, at the very least). IF it does work some of the time, then when it displays the code blocks to apply, it just freezes and spins when I try to apply them. If someone has experienced this before and knows a possible solution, drop me a message and I'll give it a try. &#32; submitted by &#32; /u/Jorlen [link] &#32; [comments]