---
id: inbox_a6d4182f
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t9ayg8/i_made_claude_code_aware_of_its_own_usage_limits/"
author: "/u/Inertia-UK"
published_at: 2026-05-10T16:05:13+00:00
fetched_at: 2026-05-10T22:37:16.943843+00:00
content_hash: "0227fa23983c3cca7771b4c6d9f86f4649e784be2ef0da5ab28fa2c4746d55eb"
lang: en
caption_quality: None
raw: true
topics: []
---

# I made Claude Code aware of its own usage limits

Something that's been annoying me for a while: Claude Code has no idea how much quota it's burned. You can see the usage bars in the UI, but the model itself is completely blind to them. There's no API, no tool, no hook that exposes the current rate limit state during a conversation. Turns out Anthropic returns rate limit headers on every inference response (`anthropic-ratelimit-unified-5h-utilization`, `anthropic-ratelimit-unified-7d-utilization`, etc.) — Claude Code receives them internally to render the UI bars, but never passes them anywhere the model can see. So I built a small local HTTP proxy that sits between Claude Code and `api.anthropic.com`. Claude Code already respects `ANTHROPIC_BASE_URL`, so setting that to ` http://127.0.0.1:4080\` routes all traffic through the proxy. It intercepts the response headers and writes a one-line status file to `~/.claude/usage-status.md`: ``` 5h=9% 7d=99%! overage=0% bottleneck=seven_day (10/05/2026, 16:19:04) ``` Claude can then read that file on demand, or you can inject it automatically via a `UserPromptSubmit` hook so it's present in every prompt. Add a rule to your CLAUDE.md and Claude will warn you before starting large tasks when you're close to the limit, switch to lightweight mode above 90%, or flat out refuse new implementation work at 98%. **Note:** this only works with Claude Code (the CLI). The web chat and browser extension make requests through Anthropic's own infrastructure, so there's no local proxy to intercept. **The interesting discovery:** while testing I dumped every `anthropic-ratelimit-*` header from both Opus and Sonnet requests. There are no per-model headers — one unified pool covers everything. The separate Sonnet usage bar in the Claude Code UI doesn't reflect a real separate limit. According to GitHub issue #57050, Anthropic intended to give Sonnet its own bucket (announced Nov 2025) but the backend never shipped it. Using Sonnet drains the same unified pool as Opus. The proxy is zero npm dependencies, plain Node.js stdlib. On Windows it installs as a service via NSSM. macOS and Linux setup (launchd/systemd) is in the README. https://github.com/InertiaUK/claude-quota-proxy The README also has a few example CLAUDE.md rules if you want Claude to automatically adjust its behaviour based on usage level. &#32; submitted by &#32; /u/Inertia-UK [link] &#32; [comments]