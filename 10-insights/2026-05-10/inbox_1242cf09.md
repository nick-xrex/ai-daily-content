---
id: inbox_1242cf09
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_1242cf09]]"
title: "I read threads complaining about claude every week... tf are y&#39;alls workflows?"
url: https://www.reddit.com/r/ClaudeAI/comments/1t9fyns/i_read_threads_complaining_about_claude_every/
source: reddit-claudeai
published_at: 2026-05-10T19:11:37+00:00
fetched_at: 2026-05-11T02:25:28.918862+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "一位 Fortune 500 軟體工程師（10 年經驗）針對社區對 Claude 品質下滑的抱怨提出異議，認為根本問題在於用戶工作流程而非模型退化。他強調的核心原則：(1) AI 生成的代碼完全由人類負責，必須理解並能除錯；(2) Claude 4.7 reasoning 實際在改進，但思考時間更長；(3) 不應用非確定性 AI 做確定性工作，若需確定性則應生成後審計；(4) 通過 skill、harness、平行沙箱化任務、代碼審查來提高品質。他用高性能軟體（含 ASM 分析）工作並認為 Claude 大幅節省時間。"
key_points:
  - "Claude 4.7 的品質未下降，推理更深但速度更慢；需要人類負責審查生成的代碼"
  - "應避免用非確定性 AI 執行需要確定性保證的工作；若需確定性應分離為「生成 + 審計」兩步"
  - "有效工作流：skills 與 harness 為上下文、平行沙箱化任務、人工代碼審查和調整，而非完全信任 AI"
tags: [ai-engineering-practices, code-review, workflow-design]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## I read threads complaining about claude every week... tf are y'alls workflows?

一位 Fortune 500 軟體工程師（10 年經驗）針對社區對 Claude 品質下滑的抱怨提出異議，認為根本問題在於用戶工作流程而非模型退化。他強調的核心原則：(1) AI 生成的代碼完全由人類負責，必須理解並能除錯；(2) Claude 4.7 reasoning 實際在改進，但思考時間更長；(3) 不應用非確定性 AI 做確定性工作，若需確定性則應生成後審計；(4) 通過 skill、harness、平行沙箱化任務、代碼審查來提高品質。他用高性能軟體（含 ASM 分析）工作並認為 Claude 大幅節省時間。

### 重點
- Claude 4.7 的品質未下降，推理更深但速度更慢；需要人類負責審查生成的代碼
- 應避免用非確定性 AI 執行需要確定性保證的工作；若需確定性應分離為「生成 + 審計」兩步
- 有效工作流：skills 與 harness 為上下文、平行沙箱化任務、人工代碼審查和調整，而非完全信任 AI

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t9fyns/i_read_threads_complaining_about_claude_every/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I read threads complaining about claude every week... tf are y'alls workflows?

For context: I'm a software eng @ a fortune 500/FAANG tier company. We use AI. We treat all ai code with humans as the bottleneck. That is: You generate AI code, you own it. It has bugs? It's your bug. Claude has only gotten better. 4.7 reasoning has only improved, albeit it thinks more. My question is: what the hell are y'all up to that I constantly hear things like claude broke and everything sucks? You need to review the code. YOU need to understand what claude outputs. AI is nondeterministic, so I don't know why people are creating agentic flows for deterministic work. Need determinism? Generate an audit the code man. What are people's workflows here that I constantly hear about degraded quality? Personally I just create plenty of skills and harnesses for information that it needs, I set off parallel tasks that are sandboxed from each other (E.g using a worktree, different folder, whatever your taste is), I review the code, I tweak it myself manually.. and that's it. At the end of the day, I've been a software engineer for 10 years, I understand anything claude generates is something I have to own and be able to debug eventually myself if the world suddenly gets rid of AI (which we know it won't, but it's the sentiment that should be held). I'm not coming from a place of reprimanding, truly I'm not, but I just don't see how it's gotten worse. I work on very high perf software and claude has helped a lot in saving me time on ASM analysis and algorithmic reasoning for things where throughput matters. &#32; submitted by &#32; /u/monoidalendo [link] &#32; [comments]

</details>