---
id: inbox_f62892c1
source: hackernews
source_type: hn
url: "https://systima.ai/blog/claude-code-vs-opencode-token-overhead"
author: "systima"
published_at: 2026-07-12T18:25:51+00:00
fetched_at: 2026-07-13T00:41:21.682044+00:00
content_hash: "6a83bdc995d1177185ddbccc618d224e01387bb7e76b036813100a0811437633"
lang: en
caption_quality: None
raw: true
topics: []
---

# Claude Code sends 33k tokens before reading the prompt; OpenCode sends 7k

This started based off of a hunch. We usually use OpenCode, but were &#x27;forced&#x27; to use Claude Code for a while due to issues with Meridian. In that time, we saw the usage meter rise much, much more quickly than when using OpenCode. This was the initial anecdotal evidence, but we undertook this small study to collect empirical data: We added logging between the agentic coding tool (Claude Code and OpenCode) and Anthropic&#x27;s endpoint, and captured all requests (and the returned usage blocks). With one caveat (toward the end of the post) we found unambiguously that Claude Code was far more inefficient in terms of its cache strategy and its harness token usage than OpenCode.