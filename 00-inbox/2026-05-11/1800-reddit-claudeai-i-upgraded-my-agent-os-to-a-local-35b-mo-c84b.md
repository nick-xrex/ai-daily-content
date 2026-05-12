---
id: inbox_09388ba8
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t9tqz6/i_upgraded_my_agent_os_to_a_local_35b_model_and/"
author: "/u/TheOnlyVibemaster"
published_at: 2026-05-11T05:20:39+00:00
fetched_at: 2026-05-11T18:00:40.248223+00:00
content_hash: "c84bbfa6dc34057bc69bcccf1f9d57eeceba98da267b92f61957ca7676745e5e"
lang: en
caption_quality: None
raw: true
topics: []
---

# I upgraded my Agent OS to a local 35B model and its code failure rate dropped to 0%

I’ve been obsessed with autonomous agents lately, but it got tiring when they keep hitting walls because they didn't have the right &quot;tools&quot; or because their context window turned to mush after an hour. I’ve found that local multi-agent systems where agents are driven by an aversive state (a suffering system) to autonomously write, sandbox, and hot-load their own tools so they don't hit walls has worked quite well. When an agent encounters something it hasn’t seen before, it builds a new tool for the job, tests it in a sandbox, registers it, lets the other agents know, then keeps rolling. It’s able to build an infinite library of anything it may need in the future, completely autonomously without a human ever in the loop. Repo: https://github.com/ninjahawk/hollow-agentOS Isn’t letting local LLMs write their own code at runtime going to get too chaotic and brick the OS fast? With a small model (like the 9B fallback), possibly. Under high system stress, a 9B model panics. It rushes, hallucinates invalid function calls, and tries to force broken syntax past the gates. But I just scaled the default runtime engine to Qwen 3.6 35B A3B (MoE with 3B active params). The shift in architectural discipline isn’t just a linear upgrade in intelligence, it completely changed how the system executes autonomy. A few things this model upgrade solved: Panic vs. Re-evaluation: Instead of blindly rushing out messy scripts under high stress, the 35B model pauses. It actively re-evaluates its previous failed outputs and forces itself into deep internal verification loops before presenting a file change. 0% Failure Rate: The OS routes all code through a brutal 5-layer validation gate. With smaller weights, tools frequently died in the sandbox. With Qwen 3.6 35B, I have yet to observe a single line of code that doesn't work as intended successfully cross the gates. It hit a 100% success rate. The Frontier Ramp-Up: By the end of the month, I am plugging full Claude and Codex into the architecture. To make sure a frontier model doesn't get out of control or override its host environment, I am building hyper-isolated mini-VM wrappers so they execute in total isolation. Check out the repo here and throw it a star if you think the concept is cool. I'd love to hear your thoughts, have you noticed a similar leap in logical self-correction when crossing the ~30B parameter threshold, or are you strictly relying on API-driven frontier models? &#32; submitted by &#32; /u/TheOnlyVibemaster [link] &#32; [comments]