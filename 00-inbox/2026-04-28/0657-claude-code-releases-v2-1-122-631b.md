---
id: inbox_24cd06fb
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.122"
author: "ashwin-ant"
published_at: 2026-04-28T22:05:15+00:00
fetched_at: 2026-04-29T06:57:45.600022+00:00
content_hash: "631b87aa67b2f5ff2252fc4b32ce531fdae78ed32c9d5e5158a150e4ec6b846d"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.122

<h2>What's changed</h2>
<ul>
<li>Added <code>ANTHROPIC_BEDROCK_SERVICE_TIER</code> environment variable to select a Bedrock service tier (<code>default</code>, <code>flex</code>, or <code>priority</code>), sent as the <code>X-Amzn-Bedrock-Service-Tier</code> header</li>
<li>Pasting a PR URL into the <code>/resume</code> search box now finds the session that created that PR (GitHub, GitHub Enterprise, GitLab, and Bitbucket)</li>
<li><code>/mcp</code> now shows claude.ai connectors hidden by a manually-added server with the same URL, with a hint to remove the duplicate</li>
<li>Clarified the <code>/mcp</code> message shown when an MCP server is still unauthorized after the browser sign-in flow</li>
<li>OpenTelemetry: numeric attributes on <code>api_request</code>/<code>api_error</code> log events are now emitted as numbers, not strings</li>
<li>OpenTelemetry: added <code>claude_code.at_mention</code> log event for <code>@</code>-mention resolution</li>
<li>Fixed <code>/branch</code> producing forks that fail with "tool_use ids were found without tool_result blocks" when the source session contained entries from rewound timelines</li>
<li>Fixed <code>/model</code> not showing the Effort option for Bedrock application inference profile ARNs, and those ARNs not receiving <code>output_config.effort</code></li>
<li>Fixed Vertex AI / Bedrock returning <code>invalid_request_error: output_config: Extra inputs are not permitted</code> on session-title generation and other structured-output queries</li>
<li>Fixed Vertex AI <code>count_tokens</code> endpoint returning 400 errors for users behind proxy gateways</li>
<li>Fixed <code>spinnerTipsOverride.excludeDefault</code> not suppressing the time-based spinner tips</li>
<li>Fixed ToolSearch missing MCP tools that connected after session start in nonblocking mode</li>
<li>Fixed <code>!exit</code> / <code>!quit</code> in bash mode terminating the CLI instead of running as a shell command</li>
<li>Fixed images sent to newer models being resized to 2576px per side instead of the correct 2000px maximum</li>
<li>Fixed remote control session idle status redrawing twice per second, which could flood <code>tmux -CC</code> control pipes and pause the terminal</li>
<li>Fixed assistant messages appearing blank in some sessions due to a stale view preference</li>
<li>Fixed a malformed hooks entry in <code>settings.json</code> no longer invalidating the entire file</li>
<li>Voice mode: keybindings bound to Caps Lock now show an error since terminals don't deliver Caps Lock as a key event</li>
</ul>