---
id: inbox_71303bee
date: 2026-05-18
source_ref: "[[00-inbox/2026-05-18/0201-reddit-localllama-if-you-use-continue-dev-and-qwen-3-6-den-10c1]]"
title: "If you use continue.dev and Qwen 3.6 (dense / MoE) - I could use your help"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tgkyud/if_you_use_continuedev_and_qwen_36_dense_moe_i/
source: reddit-localllama
published_at: 2026-05-18T12:21:41+00:00
fetched_at: 2026-05-19T02:11:10.710132+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: ""
key_points:
tags: []
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## If you use continue.dev and Qwen 3.6 (dense / MoE) - I could use your help



### 重點

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tgkyud/if_you_use_continuedev_and_qwen_36_dense_moe_i/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Someone suggested I give Continue (Vscode extension) a try. I've been using Roo / Zoo now and liking it but it is pretty tough on context and I was told continue has more control over it. Anyways, I got it working, at the core... they talk to one another but something strange is happening. I've tried both Qwen 3.6 models; the dense 27b and 35B/A3B. If you ask it simple chats, no problem. But if you then call it to do any coding calls, or file reads, it'll think and then just.. stop. The actual output doesn't come out. I can see the thinking block but not the output. The template is fine, works everywhere else including via Roo and I've played about with the max reasoning budget setting of llama.cpp (docker server version). I know the reasoning budget settings works because if I drop into llama's own interface and ask it to describe quantum mechanics, it abruptly halts the thinking process at exactly the same token use amount (watching it stop Qwen at 1024 has been amusing, at the very least). IF it does work some of the time, then when it displays the code blocks to apply, it just freezes and spins when I try to apply them. If someone has experienced this before and knows a possible solution, drop me a message and I'll give it a try. &#32; submitted by &#32; /u/Jorlen [link] &#32; [comments]

</details>