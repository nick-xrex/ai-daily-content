---
id: inbox_bdcbcccc
date: 2026-05-06
source_ref: "[[00-inbox/.../inbox_bdcbcccc]]"
title: "What&#39;s new in CC 2.1.128 (+1406 tokens)"
url: https://www.reddit.com/r/ClaudeAI/comments/1t50fzd/whats_new_in_cc_21128_1406_tokens/
source: reddit-claudeai
published_at: 2026-05-06T02:46:38+00:00
fetched_at: 2026-05-06T13:31:54.854995+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 發布版本 2.1.128，相比前版本新增 1406 tokens 的系統提示內容。本次更新涵蓋代理、API、文檔等多層面。代理功能方面，背景任務代理指令得到顯著改進，新增進度敘述、工具結果自動重述、噪音調查委派等機制，以及明確的狀態信號（result: / needs input: / failed:）。工具層面新增 RemoteTrigger API，允許排程和管理遠程代理例程而無需暴露 OAuth token。模型層面，Claude Sonnet 4 與 Opus 4 被標記為棄用，官方推薦升級至 Opus 4.7 或 Sonnet 4.6。API 方面，Claude SDK 跨 Python、TypeScript、C#、Go、Java、PHP、Ruby 等語言新增結構化指引。"
key_points:
  - "Claude Sonnet 4 與 Opus 4 棄用，推薦升級至 Opus 4.7 或 Sonnet 4.6"
  - "背景代理指令改進：新增 result: / needs input: / failed: 明確狀態信號機制"
  - "RemoteTrigger API 新增，支援無 OAuth 暴露的排程遠程代理例程管理"
tags: [claude-code-release, version-2.1.128, api-updates]
topics: []
importance: 4
novelty: 5
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## What's new in CC 2.1.128 (+1406 tokens)

Claude Code 發布版本 2.1.128，相比前版本新增 1406 tokens 的系統提示內容。本次更新涵蓋代理、API、文檔等多層面。代理功能方面，背景任務代理指令得到顯著改進，新增進度敘述、工具結果自動重述、噪音調查委派等機制，以及明確的狀態信號（result: / needs input: / failed:）。工具層面新增 RemoteTrigger API，允許排程和管理遠程代理例程而無需暴露 OAuth token。模型層面，Claude Sonnet 4 與 Opus 4 被標記為棄用，官方推薦升級至 Opus 4.7 或 Sonnet 4.6。API 方面，Claude SDK 跨 Python、TypeScript、C#、Go、Java、PHP、Ruby 等語言新增結構化指引。

### 重點
- Claude Sonnet 4 與 Opus 4 棄用，推薦升級至 Opus 4.7 或 Sonnet 4.6
- 背景代理指令改進：新增 result: / needs input: / failed: 明確狀態信號機制
- RemoteTrigger API 新增，支援無 OAuth 暴露的排程遠程代理例程管理

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t50fzd/whats_new_in_cc_21128_1406_tokens/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# What's new in CC 2.1.128 (+1406 tokens)

<!-- SC_OFF --><div class="md"><ul> <li>NEW: Agent Prompt: Background job agent instructions — Replaces the background-job behavior system prompt with built-in background-agent instructions for progress narration, tool-result restatement, noisy-investigation delegation, and explicit result:, needs input:, or failed: status signals.</li> <li>NEW: Agent Prompt: Onboarding guide share link close — Adds onboarding-guide closing instructions that upload finalized ONBOARDING.md with ShareOnboardingGuide, handle existing-guide and unavailable-tool cases, and return the generated team share link.</li> <li>NEW: Tool Description: RemoteTrigger prompt — Describes the claude.ai remote-trigger API tool for listing, reading, creating, updating, and running scheduled remote agent routines without exposing OAuth tokens.</li> <li>REMOVED: Agent Prompt: Session memory update instructions — Removed the conversation-session notes update prompt that edited structured session memory files during chats.</li> <li>REMOVED: Data: Session memory template — Removed the structured summary.md session memory template.</li> <li>REMOVED: System Prompt: Background job behavior — Removed the standalone background-job behavior prompt; its conventions now live in the new built-in background job agent instructions.</li> <li>Data: Claude API SDK references — Added structured refusal stop-details guidance across Python, TypeScript, C#, Go, Java, PHP, and Ruby, and added programmatic API error type guidance for Java, PHP, Ruby, and the HTTP error reference.</li> <li>Data: Claude API reference — C# — Documents beta C# tool-runner and Managed Agents support via BetaToolRunner and client.Beta.Agents/Sessions/Environments.</li> <li>Data: Claude API reference — Go — Adds typed model constants, updates adaptive thinking syntax, and documents the beta advisor tool parameter.</li> <li>Data: Claude API reference — Java — Updates the documented SDK version from 2.17.0 to 2.27.0 and adds beta advisor tool guidance.</li> <li>Data: Claude model catalog — Marks Claude Sonnet 4 and Claude Opus 4 as deprecated, recommends Opus 4.7 or Sonnet 4.6 replacements, and updates older Sonnet replacement guidance to Sonnet 4.6.</li> <li>Data: Managed Agents references — Updates Python and TypeScript examples to use client.beta.sessions.events.stream and the current custom-tool event name field.</li> <li>Data: Tool use concepts — Adds beta server-side advisor tool documentation, including required model selection, optional fields, and the advisor-tool-2026-03-01 beta header.</li> <li>Skill: Building LLM-powered applications with Claude — Refreshes the current-model table for Opus 4.7, Opus 4.6, Sonnet 4.6, and Haiku 4.5; updates default model-ID examples; and notes beta C# support for tool running and Managed Agents.</li> <li>Skill: Model migration guide — Adds Opus 4.7 as the recommended Opus 4.6 migration target and adds a tuning check to parse tool inputs as JSON rather than matching serialized raw strings.</li> <li>System Prompt: Agent thread notes — Instructs agent threads to return reports, summaries, findings, and analysis directly in the final message instead of writing .md files for the parent agent to read.</li> <li>Tool Description: Edit — Hardcodes the Read-output line-number prefix format as “line number + tab” in indentation-preservation guidance.</li> <li>Tool Description: ReadFile — Always appends the additional read note placeholder at the end of the empty-file warning instead of gating it behind a separate conditional helper.</li> </ul> <p>Details: <a href="https://github.com/Piebald-AI/claude-code-system-prompts/releases/tag/v2.1.128">https://github.com/Piebald-AI/claude-code-system-prompts/releases/tag/v2.1.128</a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Dramatic_Squash_3502"> /u/Dramatic_Squash_3502 </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t50fzd/whats_new_in_cc_21128_1406_tokens/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t50fzd/whats_new_in_cc_21128_1406_tokens/">[comments]</a></span>

</details>