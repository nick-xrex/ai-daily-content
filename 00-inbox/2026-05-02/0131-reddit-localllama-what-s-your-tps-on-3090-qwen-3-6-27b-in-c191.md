---
id: inbox_7478f823
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t1nts8/whats_your_tps_on_3090_qwen_36_27b_in_real_tasks/"
author: "/u/Anbeeld"
published_at: 2026-05-02T11:54:05+00:00
fetched_at: 2026-05-03T01:31:38.486306+00:00
content_hash: "c191f075001d9e19c050706de491782b662ce2d5bd70bb3638a1ff6c6871d827"
lang: en
caption_quality: None
raw: true
topics: []
---

# What's your tps on 3090 + Qwen 3.6 27B in real tasks?

<!-- SC_OFF --><div class="md"><p>I struggle to wrap my head around all this. My goal is local agent to solve low complexity tasks, in the same harness where I would use frontier models. So naturally this means a large context window, because low complexity can mean a simple-ish fix in a large codebase, rather than just generating some nonsense from zero.</p> <p>So initially I went for Tom's turboquant plus fork of llama.cpp (I'm on Windows) with Qwen 3.6 Q4 and IQ4 models and 200k context window. Well it worked, it can read the entirety of example project I gave to it and make an audit (as much as it's capable of making it). But deep into context window the speed is just sad, like 10-11 tps, or even lower?</p> <p>So I went into a rabbit hole of all the posts there all saying they have 85-100 tps on a single 3090 with a 5 billion context window or so. I've tried WSL2+vLLM with MTP and Genesis patches. Well it works in a sense that it launches but I'm OOM at any adequate context window and also it seems like there are tool issues and whatnot.</p> <p>I've tried Luce DFlash solution and it turned out they didn't even have a working server solution. I made 2 PRs into it that fixed huge VRAM issues but then it turned out it doesn't format thinking right and can't use tools whatsoever. Oh well. Was fast in the &quot;hi&quot; chat at least.</p> <p>Now I'm trying some other llama.cpp forks and modifying them to fix obvious issues they have, but at this point I have to question it all.</p> <p>What's your tps on 3090 + Qwen 3.6 27B in real tasks? Like real coding tasks with many thousands of context, in proper harness? From what I read all these technologies like MTP and DFlash degrade very very fast with context as predicting correctly becomes very hard as the prediction model only sees a small part of the context at any time. Is that right?</p> <p>But I also see people claiming they maintain like 30 tps on long chats. The &quot;chats&quot; is key there. All these benchmarks illustrate numbers based on feeding a model one prompt. Which is so so so much faster than multi-step chats. But in real agentic usage you often need this back-and-forth feedback.</p> <p>And yes I do need thinking, it's crucial for coding tasks, but seems like it ruins prediction systems speed even further?</p> <p>So tell me, is it skill issue or it really isn't as simple as these posts make it seem to be?</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Anbeeld"> /u/Anbeeld </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1nts8/whats_your_tps_on_3090_qwen_36_27b_in_real_tasks/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1nts8/whats_your_tps_on_3090_qwen_36_27b_in_real_tasks/">[comments]</a></span>