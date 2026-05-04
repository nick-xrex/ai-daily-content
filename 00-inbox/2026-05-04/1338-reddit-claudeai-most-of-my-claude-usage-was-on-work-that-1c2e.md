---
id: inbox_16202cd3
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t3elab/most_of_my_claude_usage_was_on_work_that_didnt/"
author: "/u/petburiraja"
published_at: 2026-05-04T11:12:10+00:00
fetched_at: 2026-05-04T13:38:39.516396+00:00
content_hash: "1c2e459d21006b847c7c2dff24fc78b25f3bc8a12668eaac56e3a7ee7224c946"
lang: en
caption_quality: None
raw: true
topics: []
---

# Most of my Claude usage was on work that didn't need Claude. Cut my bill 60x on bulk tasks with a tiny side model.

<!-- SC_OFF --><div class="md"><p>I looked at what was actually eating my Claude usage and it was embarrassing. Classifying files. Reformatting json. Pulling fields out of text. Summarizing docs I was going to skim anyway. None of that needed Sonnet. All of it cost the same as the work that did.</p> <p>Tried the obvious fixes first. Switching to Haiku for simple stuff (still wasteful at volume). Tighter prompts (helps a little). /compact (delays the problem). None of it changed the shape of the spend.</p> <p>What actually worked: a small cheap model running as a side worker, with one rule in CLAUDE.md telling Claude not to do the mechanical stuff itself.</p> <p>The setup is one tool. Send it text, get text back. Claude calls it for the bounded mechanical work I'd review anyway. Default model is DeepSeek V4 Flash because it's cheap and has 1M context, but the endpoint is one config line and works with anything openai-compatible (local ollama, vllm, lm studio).</p> <p><strong>3 weeks of real usage:</strong></p> <ul> <li>217 mechanical calls offloaded</li> <li>DeepSeek total spend: $0.41</li> <li>Same workload on Sonnet would have been roughly $7</li> </ul> <p>The CLAUDE.md rule that actually works is negative framing. Not &quot;use deepseek for X&quot; but &quot;do NOT use Claude for: json formatting, field extraction, file classification, summarization you will review anyway.&quot; Positive framing got ignored maybe 30% of the time. Deny list catches it.</p> <p>It's a supervised worker, not an agent. No tool calls, no file access, no chains. Latency 3-25s. You review the output. That's the whole shape.</p> <p>Repo with setup steps: <a href="https://github.com/arizen-dev/deepseek-mcp">https://github.com/arizen-dev/deepseek-mcp</a> (MIT, Python 3.10+)</p> <p>Happy to answer questions about the routing rules or the model choice.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/petburiraja"> /u/petburiraja </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3elab/most_of_my_claude_usage_was_on_work_that_didnt/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3elab/most_of_my_claude_usage_was_on_work_that_didnt/">[comments]</a></span>