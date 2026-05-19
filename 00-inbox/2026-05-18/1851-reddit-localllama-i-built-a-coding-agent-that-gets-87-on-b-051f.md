---
id: inbox_4984f599
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tgecrq/i_built_a_coding_agent_that_gets_87_on_benchmarks/"
author: "/u/Glittering_Focus1538"
published_at: 2026-05-18T06:38:11+00:00
fetched_at: 2026-05-18T18:51:02.576334+00:00
content_hash: "051f072dc103828a7512b74922cbefe89b8ae8be8e185ca03b70332d6f16e2e8"
lang: en
caption_quality: None
raw: true
topics: []
---

# I built a coding agent that gets 87% on benchmarks with a 4B parameter model, here's how

I was frustrated that every coding agent (OpenCode, Cursor, Claude Code) assumes you're running GPT-5.4 or Claude Opus. If you try them with a local model like Gemma or Qwen they fall apart. I find that often tool calls fail, context overflows, multi-step tasks collapse. So I built SmallCode. It's designed from the ground up for small local models. The result: 87/100 benchmark tasks pass with a Gemma 4 model that only activates 4B parameters per token. OpenCode scores ~75% with 14B models. The harness does the heavy lifting, not the model size. How it works (the tricks that make small models reliable): Compound tools: Instead of making the model chain 4 tool calls (find file → read file → edit file → verify), SmallCode gives it one tool that does all 4. Small models lose coherence after 3+ sequential calls. This cuts failures in half. Improvement loop: Every time the model writes code, SmallCode instantly compiles/lints it. If it fails, it feeds the errors back automatically. The model doesn't need to be smart enough to get it right first try — it just needs to fix errors when shown them. Decompose on failure: If the model fails the same thing twice, SmallCode stops retrying and instead breaks the problem into smaller pieces. &quot;Fix this 200-line file&quot; becomes &quot;fix line 45 only.&quot; Escalation: If even decompose fails and you have a Claude/OpenAI key configured, it auto-escalates to the bigger model for just that one task. You stay local 95% of the time, cloud 5%. Token budgeting: Small models have 32k-256k context. SmallCode never dumps a whole file in. It summarizes, truncates, and manages every token so the model never sees &quot;...&quot; truncation in the middle of important code. Code graph: Instead of grep-searching your codebase, SmallCode indexes your code into a symbol graph (functions, classes, who-calls-what). When you ask &quot;how does auth work,&quot; it walks the graph and returns just the relevant connected code — not 15 random file snippets. What it looks like: Full-screen terminal UI (like OpenCode/vim), scrollable chat, command palette with / , plugin system, persistent memory across sessions. What it doesn't do: No LSP integration (yet) No multi-session (yet) No desktop app Doesn't compete with Claude Code for frontier model users Install: npm install -g smallcode cd your-project smallcode Point it at LM Studio, Ollama, or any OpenAI-compatible endpoint. MIT licensed, everything's on GitHub: https://github.com/Doorman11991/smallcode Happy to answer questions about the architecture or benchmark methodology. &#32; submitted by &#32; /u/Glittering_Focus1538 [link] &#32; [comments]