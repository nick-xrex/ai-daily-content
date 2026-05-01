---
id: inbox_8e64b793
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t0fuwj/claude_code_usage_spike_from_longcontext_cache/"
author: "/u/Different_Try_1269"
published_at: 2026-05-01T01:56:53+00:00
fetched_at: 2026-05-01T12:57:19.188438+00:00
content_hash: "8245dd5b49c857916d36b08954c91b18a0b27117dab9177a4e2ee4d4b809ab94"
lang: en
caption_quality: None
raw: true
topics: []
---

# Claude Code usage spike from long-context cache writes?

<!-- SC_OFF --><div class="md"><p>I hit my Claude Code 5-hour limit unexpectedly and checked the local session JSONL.</p> <p>The `/usage` screen said most usage came from:</p> <p>- “subagent-heavy sessions”</p> <p>- sessions active for 8+ hours</p> <p>- `&gt;150k context`</p> <p>But the subagent table only showed `codebase-explorer: 1%`, so subagents don’t seem to explain</p> <p>the spike.</p> <p>After deduplicating local records by `requestId`, the main session had about 140M cache-read</p> <p>tokens. The surprising part is that some of the final requests recreated a huge 1-hour prompt</p> <p>cache of around 475k tokens each.</p> <p>Using public API pricing, a 475k 1-hour cache write should be only a few dollars API-</p> <p>equivalent. But in Claude Code, one of these final requests seemed to consume a very large</p> <p>fraction of my 5-hour limit.</p> <p>I use a pro subscription and only use sonnet-4.6 model.</p> <p>So I’m wondering:</p> <p>Is Claude Code intentionally weighting long-context / 1-hour cache writes much more heavily</p> <p>than API pricing, or could this be a usage accounting / attribution bug?</p> <p>Has anyone else seen a large Claude Code usage jump after a long-running session with `&gt;150k`</p> <p>context?</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Different_Try_1269"> /u/Different_Try_1269 </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t0fuwj/claude_code_usage_spike_from_longcontext_cache/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t0fuwj/claude_code_usage_spike_from_longcontext_cache/">[comments]</a></span>