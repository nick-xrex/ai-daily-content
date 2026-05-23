---
id: inbox_8472d81a
source: hermes-agent-releases
source_type: rss
url: "https://github.com/NousResearch/hermes-agent/releases/tag/v2026.4.23"
author: "teknium1"
published_at: 2026-04-23T22:32:13+00:00
fetched_at: 2026-05-22T18:00:31.401016+00:00
content_hash: "6d02b810f516d458f68a7011ad65d742204d0f608bcc172b03562dfe59a233da"
lang: en
caption_quality: None
raw: true
topics: []
---

# Hermes Agent v0.11.0 (2026.4.23)

Hermes Agent v0.11.0 (v2026.4.23) 
 Release Date: April 23, 2026 
 Since v0.9.0: 1,556 commits · 761 merged PRs · 1,314 files changed · 224,174 insertions · 29 community contributors (290 including co-authors) 
 
 The Interface release — a full React/Ink rewrite of the interactive CLI, a pluggable transport architecture underneath every provider, native AWS Bedrock support, five new inference paths, a 17th messaging platform (QQBot), a dramatically expanded plugin surface, and GPT-5.5 via Codex OAuth. 
 
 This release also folds in all the highlights deferred from v0.10.0 (which shipped only the Nous Tool Gateway) — so it covers roughly two weeks of work across the whole stack. 
 
 ✨ Highlights 
 
 
 New Ink-based TUI — hermes --tui is now a full React/Ink rewrite of the interactive CLI, with a Python JSON-RPC backend ( tui_gateway ). Sticky composer, live streaming with OSC-52 clipboard support, stable picker keys, status bar with per-turn stopwatch and git branch, /clear confirm, light-theme preset, and a subagent spawn observability overlay. ~310 commits to ui-tui/ + tui_gateway/ . ( @OutThisLife + Teknium) 
 
 
 Transport ABC + Native AWS Bedrock — Format conversion and HTTP transport were extracted from run_agent.py into a pluggable agent/transports/ layer. AnthropicTransport , ChatCompletionsTransport , ResponsesApiTransport , and BedrockTransport each own their own format conversion and API shape. Native AWS Bedrock support via the Converse API ships on top of the new abstraction. ( #10549 , #13347 , #13366 , #13430 , #13805 , #13814 — @kshitijk4poor + Teknium) 
 
 
 Five new inference paths — Native NVIDIA NIM ( #11774 ), Arcee AI ( #9276 ), Step Plan ( #13893 ), Google Gemini CLI OAuth ( #11270 ), and Vercel ai-gateway with pricing + dynamic discovery ( #13223 — @jerilynzheng ). Plus Gemini routed through the native AI Studio API for better performance ( #12674 ). 
 
 
 GPT-5.5 over Codex OAuth — OpenAI's new GPT-5.5 reasoning model is now available through your ChatGPT Codex OAuth, with live model discovery wired into the model picker so new OpenAI releases show up without catalog updates. ( #14720 ) 
 
 
 QQBot — 17th supported platform — Native QQBot adapter via QQ Official API v2, with QR scan-to-configure setup wizard, streaming cursor, emoji reactions, and DM/group policy gating that matches WeCom/Weixin parity. ( #9364 , #11831 ) 
 
 
 Plugin surface expanded — Plugins can now register slash commands ( register_command ), dispatch tools directly ( dispatch_tool ), block tool execution from hooks ( pre_tool_call can veto), rewrite tool results ( transform_tool_result ), transform terminal output ( transform_terminal_output ), ship image_gen backends, and add custom dashboard tabs. The bundled disk-cleanup plugin is opt-in by default as a reference implementation. ( #9377 , #10626 , #10763 , #10951 , #12929 , #12944 , #12972 , #13799 , #14175 ) 
 
 
 /steer — mid-run agent nudges — /steer &lt;prompt&gt; injects a note that the running agent sees after its next tool call, without interrupting the turn or breaking prompt cache. For when you want to course-correct an agent in-flight. ( #12116 ) 
 
 
 Shell hooks — Wire any shell script as a Hermes lifecycle hook (pre_tool_call, post_tool_call, on_session_start, etc.) without writing a Python plugin. ( #13296 ) 
 
 
 Webhook direct-delivery mode — Webhook subscriptions can now forward payloads straight to a platform chat without going through the agent — zero-LLM push notifications for alerting, uptime checks, and event streams. ( #12473 ) 
 
 
 Smarter delegation — Subagents now have an explicit orchestrator role that can spawn their own workers, with configurable max_spawn_depth (default flat). Concurrent sibling subagents share filesystem state through a file-coordination layer so they don't clobber each other's edits. ( #13691 , #13718 ) 
 
 
 Auxiliary models — configurable UI + main-model-first — hermes model has a dedicated "Configure auxiliary models" screen for per-task overrides (compression, vision, session_search, title_generation). auto routing now defaults to the main model for side tasks across all users (previously aggregator users were silently routed to a cheap provider-side default). ( #11891 , #11900 ) 
 
 
 Dashboard plugin system + live theme switching — The web dashboard is now extensible. Third-party plugins can add custom tabs, widgets, and views without forking. Paired with a live-switching theme system — themes now control colors, fonts, layout, and density — so users can hot-swap the dashboard look without a reload. Same theming discipline the CLI has, now on the web. ( #10951 , #10687 , #14725 ) 
 
 
 Dashboard polish — i18n (English + Chinese), react-router sidebar layout, mobile-responsive, Vercel deployment, real per-session API call tracking, and one-click update + gateway restart buttons. ( #9228 , #9370 , #9453 , #10686 , #13526 , #14004 — @austinpickett + @DeployFaith + Teknium) 
 
 
 
 🏗️ Core Agent &amp; Architecture 
 Transport Layer (NEW) 
 
 Transport ABC abstracts format conversion and HTTP transport from run_agent.py into agent/transports/ ( #13347 ) 
 AnthropicTransport — Anthropic Messages API path ( #13366 , @kshitijk4poor ) 
 ChatCompletionsTransport — default path for OpenAI-compatible providers ( #13805 ) 
 ResponsesApiTransport — OpenAI Responses API + Codex build_kwargs wiring ( #13430 , @kshitijk4poor ) 
 BedrockTransport — AWS Bedrock Converse API transport ( #13814 ) 
 
 Provider &amp; Model Support 
 
 Native AWS Bedrock provider via Converse API ( #10549 ) 
 NVIDIA NIM native provider (salvage of #11703 ) ( #11774 ) 
 Arcee AI direct provider ( #9276 ) 
 Step Plan provider (salvage #6005 ) ( #13893 , @kshitijk4poor ) 
 Google Gemini CLI OAuth inference provider ( #11270 ) 
 Vercel ai-gateway with pricing, attribution, and dynamic discovery ( #13223 , @jerilynzheng ) 
 GPT-5.5 over Codex OAuth with live model discovery in the picker ( #14720 ) 
 Gemini routed through native AI Studio API ( #12674 ) 
 xAI Grok upgraded to Responses API ( #10783 ) 
 Ollama improvements — Cloud provider support, GLM continuation, think=false control, surrogate sanitization, /v1 hint ( #10782 ) 
 Kimi K2.6 across OpenRouter, Nous Portal, native Kimi, and HuggingFace ( #13148 , #13152 , #13169 ) 
 Kimi K2.5 promoted to first position in all model suggestion lists ( #11745 , @kshitijk4poor ) 
 Xiaomi MiMo v2.5-pro + v2.5 on OpenRouter, Nous Portal, and native ( #14184 , #14635 , @kshitijk4poor ) 
 GLM-5V-Turbo for coding plan ( #9907 ) 
 Claude Opus 4.7 in Nous Portal catalog ( #11398 ) 
 OpenRouter elephant-alpha in curated lists ( #9378 ) 
 OpenCode-Go — Kimi K2.6 and Qwen3.5/3.6 Plus in curated catalog ( #13429 ) 
 minimax/minimax-m2.5:free in OpenRouter catalog ( #13836 ) 
 /model merges models.dev entries for lesser-loved providers ( #14221 ) 
 Per-provider + per-model request_timeout_seconds config ( #12652 ) 
 Configurable API retry count via agent.api_max_retries ( #14730 ) 
 ctx_size context length key for Lemonade server (salvage #8536 ) ( #14215 ) 
 Custom provider display name prompt ( #9420 ) 
 Recommendation badges on tool provider selection ( #9929 ) 
 Fix: correct GPT-5 family context lengths in fallback defaults ( #9309 ) 
 Fix: clamp minimal reasoning effort to low on Responses API ( #9429 ) 
 Fix: strip reasoning item IDs from Responses API input when store=False ( #10217 ) 
 Fix: OpenViking correct account default + commit session on /new and compress ( #10463 ) 
 Fix: Kimi /coding thinking block survival + empty reasoning_content + block ordering (multiple PRs) 
 Fix: don't send Anthropic thinking to api.kimi.com/coding ( #13826 ) 
 Fix: send max_tokens , reasoning_effort , and thinking for Kimi/Moonshot 
 Fix: stream reasoning content through OpenAI-compatible providers that emit it 
 
 Agent Loop &amp; Conversation 
 
 /steer &lt;prompt&gt; — mid-run agent nudges after next tool call ( #12116 ) 
 Orchestrator role + configurable spawn depth for delegate_task (default flat) ( #13691 ) 
 Cross-agent file state coordination for concurrent subagents ( #13718 ) 
 Compressor smart collapse, dedup, anti-thrashing , template upgrade, hardening ( #10088 ) 
 Compression summaries respect the conversation's language ( #12556 ) 
 Compression model falls back to main model on permanent 503/404 ( #10093 ) 
 Auto-continue interrupted agent work after gateway restart ( #9934 ) 
 Activity heartbeats prevent false gateway inactivity timeouts ( #10501 ) 
 Auxiliary models UI — dedicated screen for per-task overrides ( #11891 ) 
 Auxiliary auto routing defaults to main model for all users ( #11900 ) 
 PLATFORM_HINTS for Matrix, Mattermost, Feishu ( #14428 , @alt-glitch ) 
 Fix: reset retry counters after compression; stop poisoning conversation history ( #10055 ) 
 Fix: break compression-exhaustion infinite loop and auto-reset session ( #10063 ) 
 Fix: stale agent timeout, uv venv detection, empty response after tools ( #10065 ) 
 Fix: prevent premature loop exit when weak models return empty after substantive tool calls ( #10472 ) 
 Fix: preserve pre-start terminal interrupts ( #10504 ) 
 Fix: improve interrupt responsiveness during concurrent tool execution ( #10935 ) 
 Fix: word-wrap spinner, interruptable agent join, and delegate_task interrupt ( #10940 ) 
 Fix: /stop no longer resets the session ( #9224 ) 
 Fix: honor interrupts during MCP tool waits ( #9382 , @helix4u ) 
 Fix: break stuck session resume loops after repeated restarts ( #9941 ) 
 Fix: empty response nudge crash + placeholder leak to cron targets ( #11021 ) 
 Fix: streaming cursor sanitization to prevent message truncation (multiple PRs) 
 Fix: resolve context_length for plugin context engines ( #9238 ) 
 
 Session &amp; Memory 
 
 Auto-prune old sessions + VACUUM state.db at startup ( #13861 ) 
 Honcho overhaul — context injection, 5-tool surface, cost safety, session isolation ( #10619 ) 
 Hindsight richer session-scoped retain metadata (salvage of #6290 ) ( #13987 ) 
 Fix: deduplicate memory provider tools to prevent 400 on strict providers ( #10511 ) 
 Fix: discover user-installed memory providers from $HERMES_HOME/plugins/ ( #10529 ) 
 Fix: add on_memory_write bridge to sequential tool execution path ( #10507 ) 
 Fix: preserve session_id across previous_response_id chains in /v1/responses ( #10059 ) 
 
 
 🖥️ New Ink-based TUI 
 A full React/Ink rewrite of the interactive CLI — invoked via hermes --tui or HERMES_TUI=1 . Shipped across ~310 commits to ui-tui/ and tui_gateway/ . 
 TUI Foundations 
 
 New TUI based on Ink + Python JSON-RPC backend 
 Prettier + ESLint + vitest tooling for ui-tui/ 
 Entry split between src/entry.tsx (TTY gate) and src/app.tsx (state machine) 
 Persistent _SlashWorker subprocess for slash command dispatch 
 
 UX &amp; Features 
 
 Stable picker keys, /clear confirm, light-theme preset ( #12312 , @OutThisLife ) 
 Git branch in status bar cwd label ( #12305 , @OutThisLife ) 
 Per-turn elapsed stopwatch in FaceTicker + done-in sys line ( #13105 , @OutThisLife ) 
 Subagent spawn observability overlay ( #14045 , @OutThisLife ) 
 Per-prompt elapsed stopwatch in status bar ( #12948 ) 
 Sticky composer that freezes during scroll 
 OSC-52 clipboard support for copy across SSH sessions 
 Virtualized history rendering for performance 
 Slash command autocomplete via complete.slash RPC 
 Path autocomplete via complete.path RPC 
 Dozens of resize/ghosting/sticky-prompt fixes landed through the week 
 
 Structural Refactors 
 
 Decomposed app.tsx into app/event-handler , app/slash-handler , app/stores , app/hooks ( #14640 and surrounding) 
 Component split: branding.tsx , markdown.tsx , prompts.tsx , sessionPicker.tsx , messageLine.tsx , thinking.tsx , maskedPrompt.tsx 
 Hook split: useCompletion , useInputHistory , useQueue , useVirtualHistory 
 
 
 📱 Messaging Platforms (Gateway) 
 New Platforms 
 
 QQBot (17th platform) — QQ Official API v2 adapter with QR setup, streaming, package spl

[... truncated for safety ...]