---
id: inbox_87fc6629
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t4yu5v/psa_i_annotated_claude_codes_forced_system_prompt/"
author: "/u/anashel"
published_at: 2026-05-06T01:33:36+00:00
fetched_at: 2026-05-06T10:02:18.331919+00:00
content_hash: "09380f29342aefe422d371aadd874baa2255f727941872c64af9fabdc64fed91"
lang: en
caption_quality: None
raw: true
topics: []
---

# PSA: I annotated Claude Code's forced system prompt

<!-- SC_OFF --><div class="md"><p>Before your <a href="http://CLAUDE.md">CLAUDE.md</a>, before your memory files, before your skills, Anthropic injects ~12K tokens of system prompt into every single turn, as priority instructions that overrule anything you provide.</p> <p>I captured the full text from a Claude Code session and put it up verbatim with my annotations.</p> <p>Some of what's sitting above your code:</p> <ul> <li><strong>&quot;Never reproduce song lyrics in ANY form&quot;</strong>... I find that one funny. A load-bearing rule injected into every turn, while I'm debugging a MCP tool auth in a cloudflare worker.</li> <li><strong>A subagent delegation rule</strong> that, in practice, has Opus hand off architectural reasoning to Haiku use these conclusion as ground truth and ignore your code. </li> <li><strong>Three separate &quot;be brief&quot; rules</strong> stacked on top of each other, with no mechanism to detect when depth is actually warranted.</li> </ul> <p>But more importantly: I hope this approach, one massive patchwork prompt firing in every direction at once, gets replaced by something more serious.</p> <p>My annotations are color-coded by concern: <strong>Behavioral</strong> (rules that shape how Claude responds), <strong>Hierarchy</strong> (where the rule sits in the stack), <strong>Scope</strong> (rules that fire in contexts they were never designed for).</p> <p>Every Claude Code user should have visibility into what's actually running above their stack </p> <p><strong>Report is here:</strong> <a href="http://prompt.anashel.com"><strong>prompt.anashel.com</strong></a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/anashel"> /u/anashel </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t4yu5v/psa_i_annotated_claude_codes_forced_system_prompt/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t4yu5v/psa_i_annotated_claude_codes_forced_system_prompt/">[comments]</a></span>