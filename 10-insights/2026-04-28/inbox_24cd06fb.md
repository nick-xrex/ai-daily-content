---
id: inbox_24cd06fb
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0657-claude-code-releases-v2-1-122-631b]]"
title: "v2.1.122"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.122
source: claude-code-releases
published_at: 2026-04-28T22:05:15+00:00
fetched_at: 2026-04-29T07:01:50.783295+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.122 帶來多項功能增強與錯誤修復，涵蓋 AWS Bedrock、跨平台工作流及監測能力。新增 ANTHROPIC_BEDROCK_SERVICE_TIER 環境變數，允許選擇 Bedrock 服務層級為 default、flex 或 priority，並透過 X-Amzn-Bedrock-Service-Tier header 傳遞。/resume 指令強化，現可接受 PR URL 直接搜尋建立該 PR 的源會話，支援 GitHub、GitHub Enterprise、GitLab 及 Bitbucket 等平台。/mcp 指令改進以提示手動新增伺服器與 claude.ai 連接器重複的情況。OpenTelemetry 事件改為輸出正確的數字型別而非字符串，新增 claude_code.at_mention 事件用於追蹤提及解析。修復關鍵問題包括 Bedrock ARN 缺失 Effort 選項、Vertex AI 及 Bedrock 結構化輸出查詢回傳 400 錯誤、影像縮放錯誤（從 2576px 改為正確的 2000px）、以及遠端控制會話 idle 狀態頻繁重繪導致 tmux 控制管道阻塞。"
key_points:
  - "新增 ANTHROPIC_BEDROCK_SERVICE_TIER 支援（default/flex/priority）及 X-Amzn-Bedrock-Service-Tier header"
  - "/resume 現可直接輸入 PR URL，支援 GitHub/GitHub Enterprise/GitLab/Bitbucket 跨平台會話搜尋"
  - "修復影像縮放 2576px→2000px、Vertex AI/Bedrock structured-output 400 錯誤、remote control idle 雙倍重繪導致 tmux 阻塞等 5+ 項關鍵問題"
tags: [claude-code, bedrock, mcp, opentelemetry, feature-release]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.122

Claude Code v2.1.122 帶來多項功能增強與錯誤修復，涵蓋 AWS Bedrock、跨平台工作流及監測能力。新增 ANTHROPIC_BEDROCK_SERVICE_TIER 環境變數，允許選擇 Bedrock 服務層級為 default、flex 或 priority，並透過 X-Amzn-Bedrock-Service-Tier header 傳遞。/resume 指令強化，現可接受 PR URL 直接搜尋建立該 PR 的源會話，支援 GitHub、GitHub Enterprise、GitLab 及 Bitbucket 等平台。/mcp 指令改進以提示手動新增伺服器與 claude.ai 連接器重複的情況。OpenTelemetry 事件改為輸出正確的數字型別而非字符串，新增 claude_code.at_mention 事件用於追蹤提及解析。修復關鍵問題包括 Bedrock ARN 缺失 Effort 選項、Vertex AI 及 Bedrock 結構化輸出查詢回傳 400 錯誤、影像縮放錯誤（從 2576px 改為正確的 2000px）、以及遠端控制會話 idle 狀態頻繁重繪導致 tmux 控制管道阻塞。

### 重點
- 新增 ANTHROPIC_BEDROCK_SERVICE_TIER 支援（default/flex/priority）及 X-Amzn-Bedrock-Service-Tier header
- /resume 現可直接輸入 PR URL，支援 GitHub/GitHub Enterprise/GitLab/Bitbucket 跨平台會話搜尋
- 修復影像縮放 2576px→2000px、Vertex AI/Bedrock structured-output 400 錯誤、remote control idle 雙倍重繪導致 tmux 阻塞等 5+ 項關鍵問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.122)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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

</details>