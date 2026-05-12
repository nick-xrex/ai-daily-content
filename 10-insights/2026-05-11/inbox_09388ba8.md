---
id: inbox_09388ba8
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/1800-reddit-claudeai-i-upgraded-my-agent-os-to-a-local-35b-mo-c84b]]"
title: "I upgraded my Agent OS to a local 35B model and its code failure rate dropped to 0%"
url: https://www.reddit.com/r/ClaudeAI/comments/1t9tqz6/i_upgraded_my_agent_os_to_a_local_35b_model_and/
source: reddit-claudeai
published_at: 2026-05-11T05:20:39+00:00
fetched_at: 2026-05-11T18:19:20.709349+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用户分享本地 35B 参数模型（Qwen 3.6 35B A3B MoE）驱动的多 agent 自适应系统，agents 遇到未知问题时自主编写工具、沙盒测试、热加载，无需人工干预即可构建无限工具库。9B 模型在高压力下容易崩溃与幻觉，而 35B 模型展现出关键的行为转变：不是仓促输出代码，而是主动重新评估失败输出并进行深层内部验证。通过 5 层验证网关，35B 模型实现了 100% 代码成功率。作者观察到 ~30B 参数阈值处架构纪律发生质变，非线性升级，计划月底集成 Claude 与 Codex 前沿模型。"
key_points:
  - "Qwen 3.6 35B 相比 9B，高压力下从仓促幻觉转变为深层自我重新评估，代码通过率 0% 失败（100% 成功）"
  - "Agents 通过 aversive state 驱动自主构建工具库，5 层沙盒验证网关保障执行安全，完全自主无人工干预"
  - "~30B 参数是逻辑自制约束关键阈值；架构纪律的质变非线性，打破了对云端 API 的依赖"
tags: [local-models, multi-agent-systems, self-correction, qwen-35b, aversive-state]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## I upgraded my Agent OS to a local 35B model and its code failure rate dropped to 0%

用户分享本地 35B 参数模型（Qwen 3.6 35B A3B MoE）驱动的多 agent 自适应系统，agents 遇到未知问题时自主编写工具、沙盒测试、热加载，无需人工干预即可构建无限工具库。9B 模型在高压力下容易崩溃与幻觉，而 35B 模型展现出关键的行为转变：不是仓促输出代码，而是主动重新评估失败输出并进行深层内部验证。通过 5 层验证网关，35B 模型实现了 100% 代码成功率。作者观察到 ~30B 参数阈值处架构纪律发生质变，非线性升级，计划月底集成 Claude 与 Codex 前沿模型。

### 重點
- Qwen 3.6 35B 相比 9B，高压力下从仓促幻觉转变为深层自我重新评估，代码通过率 0% 失败（100% 成功）
- Agents 通过 aversive state 驱动自主构建工具库，5 层沙盒验证网关保障执行安全，完全自主无人工干预
- ~30B 参数是逻辑自制约束关键阈值；架构纪律的质变非线性，打破了对云端 API 的依赖

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t9tqz6/i_upgraded_my_agent_os_to_a_local_35b_model_and/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I’ve been obsessed with autonomous agents lately, but it got tiring when they keep hitting walls because they didn't have the right &quot;tools&quot; or because their context window turned to mush after an hour. I’ve found that local multi-agent systems where agents are driven by an aversive state (a suffering system) to autonomously write, sandbox, and hot-load their own tools so they don't hit walls has worked quite well. When an agent encounters something it hasn’t seen before, it builds a new tool for the job, tests it in a sandbox, registers it, lets the other agents know, then keeps rolling. It’s able to build an infinite library of anything it may need in the future, completely autonomously without a human ever in the loop. Repo: https://github.com/ninjahawk/hollow-agentOS Isn’t letting local LLMs write their own code at runtime going to get too chaotic and brick the OS fast? With a small model (like the 9B fallback), possibly. Under high system stress, a 9B model panics. It rushes, hallucinates invalid function calls, and tries to force broken syntax past the gates. But I just scaled the default runtime engine to Qwen 3.6 35B A3B (MoE with 3B active params). The shift in architectural discipline isn’t just a linear upgrade in intelligence, it completely changed how the system executes autonomy. A few things this model upgrade solved: Panic vs. Re-evaluation: Instead of blindly rushing out messy scripts under high stress, the 35B model pauses. It actively re-evaluates its previous failed outputs and forces itself into deep internal verification loops before presenting a file change. 0% Failure Rate: The OS routes all code through a brutal 5-layer validation gate. With smaller weights, tools frequently died in the sandbox. With Qwen 3.6 35B, I have yet to observe a single line of code that doesn't work as intended successfully cross the gates. It hit a 100% success rate. The Frontier Ramp-Up: By the end of the month, I am plugging full Claude and Codex into the architecture. To make sure a frontier model doesn't get out of control or override its host environment, I am building hyper-isolated mini-VM wrappers so they execute in total isolation. Check out the repo here and throw it a star if you think the concept is cool. I'd love to hear your thoughts, have you noticed a similar leap in logical self-correction when crossing the ~30B parameter threshold, or are you strictly relying on API-driven frontier models? &#32; submitted by &#32; /u/TheOnlyVibemaster [link] &#32; [comments]

</details>