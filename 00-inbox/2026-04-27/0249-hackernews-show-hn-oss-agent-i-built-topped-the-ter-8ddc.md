---
id: inbox_8f873702
source: hackernews
source_type: hn
url: "https://github.com/dirac-run/dirac"
author: "GodelNumbering"
published_at: 2026-04-27T12:35:55+00:00
fetched_at: 2026-04-28T02:49:17.958920+00:00
content_hash: "8ddcea0c84b5dacbca8cb124135cc00f08cba9ab9394495dbf096758c00e8d35"
lang: en
caption_quality: None
raw: true
topics: []
---

# Show HN: OSS Agent I built topped the TerminalBench on Gemini-3-flash-preview

Scored 65.2% vs google&#x27;s official 47.8%, and the existing top closed source model Junie CLI&#x27;s 64.3%.<p>Since there are a lot of reports of deliberate cheating on TerminalBench 2.0 lately (<a href="https:&#x2F;&#x2F;debugml.github.io&#x2F;cheating-agents&#x2F;" rel="nofollow">https:&#x2F;&#x2F;debugml.github.io&#x2F;cheating-agents&#x2F;</a>), I would like to also clarify a few things<p>1. Absolutely no {agents&#x2F;skills}.md files were inserted at any point. No cheating mechanisms whatsoever<p>2. The cli agent was run in leaderboard compliant way (no modification of resources or timeouts)<p>3. The full terminal bench run was done using the fully open source version of the agent, no difference between what is on github and what was run.<p>I was originally going to wait for it to land on the leaderboard, but it has been 8 days and the maintainers do not respond unfortunately (there is a large backlog of the pull requests on their HF) so I decided to post anyways.<p>HF PR: <a href="https:&#x2F;&#x2F;huggingface.co&#x2F;datasets&#x2F;harborframework&#x2F;terminal-bench-2-leaderboard&#x2F;discussions&#x2F;145" rel="nofollow">https:&#x2F;&#x2F;huggingface.co&#x2F;datasets&#x2F;harborframework&#x2F;terminal-ben...</a><p>It is astounding how much the harness matters, based on this and other experiments I have done.