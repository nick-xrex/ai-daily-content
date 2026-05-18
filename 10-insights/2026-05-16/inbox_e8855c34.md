---
id: inbox_e8855c34
date: 2026-05-16
source_ref: "[[00-inbox/.../inbox_e8855c34]]"
title: "How I started programming differently over the last year. What about you?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tf2cxh/how_i_started_programming_differently_over_the/
source: reddit-localllama
published_at: 2026-05-16T18:58:05+00:00
fetched_at: 2026-05-18T04:10:16.963142+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "資深開發者（36 年編程經驗）分享過去一年工作流的劇烈轉變：從 IDE autocomplete → 6 個月手寫 context 腳本 → 現在直接用 CLI coding agent。IDE 現在只佔工作 5–10%（debug、git diff、code navigation），其餘改用 LLM agent 處理（任務規劃用 plan.md、日誌分析、測試編寫）。典型反映工作模式從「IDE 中心」轉向「LLM agent 中心」的產業轉變。"
key_points:
  - "工作流進化三段：IDE autocomplete（早期）→ 手寫 context 腳本（6 個月）→ CLI LLM agent（現在）"
  - "IDE 使用率下滑至 5–10%，限於 debugging / git diff / code navigation；其餘工作轉移至 LLM agent"
  - "Plan.md 工作流：複雜任務先分解為清單，逐項讓 agent 完成，避免 context 崩塌和循環"
tags: [workflow-evolution, coding-agent, ide-replacement, plan-md]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## How I started programming differently over the last year. What about you?

資深開發者（36 年編程經驗）分享過去一年工作流的劇烈轉變：從 IDE autocomplete → 6 個月手寫 context 腳本 → 現在直接用 CLI coding agent。IDE 現在只佔工作 5–10%（debug、git diff、code navigation），其餘改用 LLM agent 處理（任務規劃用 plan.md、日誌分析、測試編寫）。典型反映工作模式從「IDE 中心」轉向「LLM agent 中心」的產業轉變。

### 重點
- 工作流進化三段：IDE autocomplete（早期）→ 手寫 context 腳本（6 個月）→ CLI LLM agent（現在）
- IDE 使用率下滑至 5–10%，限於 debugging / git diff / code navigation；其餘工作轉移至 LLM agent
- Plan.md 工作流：複雜任務先分解為清單，逐項讓 agent 完成，避免 context 崩塌和循環

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tf2cxh/how_i_started_programming_differently_over_the/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# How I started programming differently over the last year. What about you?

An interesting observation: I’ve stopped using the LLM-powered autocomplete in my IDE. At first, it was one of the key features for me. It felt extremely convenient: you start writing a function in your code, and the LLM completes it based on common sense or the context from the open tabs. But the most interesting thing is that back when LLM autocomplete was useful and in demand, I had already written a script that could go through the source files, let me select what I needed, and prepare the context to feed into an LLM chat so it could tell me what to add or fix. I worked like that for about six months. And even that is gone now. These days it’s easier to open a CLI interface with a coding agent, without even launching the IDE. You describe what you need, use @ to point it to the files it should inspect or modify, and that’s it. Everything is changing at an absolutely insane speed. Basically, the only things I still use an IDE for are nice Git diff visualization, step-by-step debugging, and the ability to click on functions and jump into their implementation. In other words, code navigation. And even that functionality is only needed in about 5-10% of my work. It’s interesting to think what comes next. What I mean is that I have an all-products subscription from JetBrains because I program in several languages at once: Java, Scala, Python, TypeScript, and Rust. But the question is: why keep paying for it? Sure, once every 2-3 months, some unclear issue appears, and debugging helps find it. On the other hand, I’ve already tried another approach: I give an LLM agent the path to the log of what is happening in the program. If it doesn’t have enough information to solve the problem, I ask it to add more logs, then I describe the problem again and ask it to understand from the logs what needs to be fixed. And of course, it’s very convenient to ask an LLM to write tests. That really is useful. If the tests fail, it looks at what it changed in the code and what it broke. When the LLM starts going in circles, I directly tell it: cover this with tests and read the logs to understand how everything works. Very convenient. One of my latest techniques is using a plan.md file. When I ask it to solve a complex task, I first ask it to create a work plan and write it into plan.md. Then I simply ask it to complete one task from that file at a time. And step by step, through small tasks, the LLM eventually gets to the result. Overall, I think the industry is changing a lot. Share your experience: how has your approach to programming changed? I’d be interested to hear how things have changed for others. But please don’t reply if you have never programmed before and have just discovered vibe coding. I’ve been programming myself since 1990, which means I wrote my first program 36 years ago... &#32; submitted by &#32; /u/ievkz [link] &#32; [comments]

</details>