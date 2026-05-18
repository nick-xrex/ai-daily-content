---
id: inbox_e8855c34
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tf2cxh/how_i_started_programming_differently_over_the/"
author: "/u/ievkz"
published_at: 2026-05-16T18:58:05+00:00
fetched_at: 2026-05-17T18:00:47.131279+00:00
content_hash: "e530fcf03bf40f4a62d1279c79ec1cb0ed319ca21a354ca1c6f754e49476c98f"
lang: en
caption_quality: None
raw: true
topics: []
---

# How I started programming differently over the last year. What about you?

An interesting observation: I’ve stopped using the LLM-powered autocomplete in my IDE. At first, it was one of the key features for me. It felt extremely convenient: you start writing a function in your code, and the LLM completes it based on common sense or the context from the open tabs. But the most interesting thing is that back when LLM autocomplete was useful and in demand, I had already written a script that could go through the source files, let me select what I needed, and prepare the context to feed into an LLM chat so it could tell me what to add or fix. I worked like that for about six months. And even that is gone now. These days it’s easier to open a CLI interface with a coding agent, without even launching the IDE. You describe what you need, use @ to point it to the files it should inspect or modify, and that’s it. Everything is changing at an absolutely insane speed. Basically, the only things I still use an IDE for are nice Git diff visualization, step-by-step debugging, and the ability to click on functions and jump into their implementation. In other words, code navigation. And even that functionality is only needed in about 5-10% of my work. It’s interesting to think what comes next. What I mean is that I have an all-products subscription from JetBrains because I program in several languages at once: Java, Scala, Python, TypeScript, and Rust. But the question is: why keep paying for it? Sure, once every 2-3 months, some unclear issue appears, and debugging helps find it. On the other hand, I’ve already tried another approach: I give an LLM agent the path to the log of what is happening in the program. If it doesn’t have enough information to solve the problem, I ask it to add more logs, then I describe the problem again and ask it to understand from the logs what needs to be fixed. And of course, it’s very convenient to ask an LLM to write tests. That really is useful. If the tests fail, it looks at what it changed in the code and what it broke. When the LLM starts going in circles, I directly tell it: cover this with tests and read the logs to understand how everything works. Very convenient. One of my latest techniques is using a plan.md file. When I ask it to solve a complex task, I first ask it to create a work plan and write it into plan.md. Then I simply ask it to complete one task from that file at a time. And step by step, through small tasks, the LLM eventually gets to the result. Overall, I think the industry is changing a lot. Share your experience: how has your approach to programming changed? I’d be interested to hear how things have changed for others. But please don’t reply if you have never programmed before and have just discovered vibe coding. I’ve been programming myself since 1990, which means I wrote my first program 36 years ago... &#32; submitted by &#32; /u/ievkz [link] &#32; [comments]