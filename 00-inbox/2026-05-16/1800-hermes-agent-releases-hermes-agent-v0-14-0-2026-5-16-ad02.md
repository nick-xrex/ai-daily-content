---
id: inbox_9211c47e
source: hermes-agent-releases
source_type: rss
url: "https://github.com/NousResearch/hermes-agent/releases/tag/v2026.5.16"
author: "teknium1"
published_at: 2026-05-16T18:55:27+00:00
fetched_at: 2026-05-22T18:00:31.387360+00:00
content_hash: "ad028f93d579b50f1a376f563fe53498f0e87f4e09e2ce7b264de2ac85dfdf37"
lang: en
caption_quality: None
raw: true
topics: []
---

# Hermes Agent v0.14.0 (2026.5.16)

Hermes Agent v0.14.0 (v2026.5.16) 
 Release Date: May 16, 2026 
 Since v0.13.0: 808 commits · 633 merged PRs · 1393 files changed · 165,061 insertions · 545 issues closed (12 P0, 50 P1) · 215 community contributors (including co-authors) 
 
 The Foundation Release — Hermes installs and runs anywhere, ships with the things you actually want to use, and stops shipping the things you don't. xAI Grok lands as a SuperGrok OAuth provider with grok-4.3 bumped to a 1M context window. A new OpenAI-compatible local proxy turns any OAuth-authed Hermes provider — Claude Pro, ChatGPT Pro, SuperGrok — into an endpoint that Codex / Aider / Cline / Continue can hit. x_search lands as a first-class X (Twitter) search tool with OAuth-or-API-key auth. The Microsoft Teams stack is wired end-to-end (Graph auth + webhook listener + pipeline runtime + outbound delivery). A debloating wave makes installs dramatically lighter — heavyweight backends now lazy-install on first use, the [all] extras drop everything covered by lazy-deps, and a tiered install falls back when a wheel rejects on your platform. pip install hermes-agent works from PyPI. The cold-start wave shaves ~19 seconds off hermes launch. Browser CDP calls are 180x faster. Two new messaging platforms (LINE + SimpleX Chat) bring the total to 22. Cross-session 1-hour Claude prompt caching, /handoff that actually transfers sessions live, native button UI for clarify on Telegram and Discord, Discord channel history backfill, LSP semantic diagnostics on every write, a unified pluggable video_generate , a computer_use cua-driver backend that finally works with non-Anthropic providers, clickable URLs in any terminal, Zed ACP Registry integration via uvx , native Windows beta, 9 new optional skills, OpenRouter Pareto Code router, huggingface/skills as a trusted default tap. 12 P0 + 50 P1 closures. 
 
 
 ✨ Highlights 
 
 
 xAI Grok via SuperGrok OAuth — and grok-4.3 jumps to a 1M context window — If you pay for SuperGrok, you can now use Grok inside Hermes by signing in with your xAI account — no API key, no separate billing. The wire-through also bumps grok-4.3 to a 1M token context window, so you can drop whole codebases or research corpora into a single prompt. Includes proper handling for entitlement errors and an SSH-to-tunnel docs page for when you're SSH'd into a remote box and need to complete the OAuth flow. ( #26534 , #26664 , #26644 , #26592 ) 
 
 
 OpenAI-compatible local proxy for OAuth providers — Run hermes proxy and you get a http://localhost:port endpoint that speaks the OpenAI API but is backed by whichever OAuth provider you're signed into — Claude Pro, ChatGPT Pro, SuperGrok. Now any tool that expects an OpenAI-compatible endpoint (Codex CLI, Aider, Cline, Continue, your custom scripts) just works with your existing subscription, no API key required. One subscription, every tool. ( #25969 ) 
 
 
 x_search — first-class X (Twitter) search tool — The agent can now search X directly without installing a skill or wiring up a custom integration. Search the timeline, find threads, surface specific posts — straight from the chat. Auth with either your X OAuth login or an API key, whichever you have. ( #26763 ) 
 
 
 Microsoft Teams — end-to-end — Hermes can now read messages from Teams and post back. The full Microsoft Graph stack lands together: auth + client foundation, a webhook listener that receives Teams events, a pipeline plugin runtime, and outbound delivery. Wire up the bot once, then chat to your agent from any Teams channel, DM, or group. (salvages of #21408 – #21411 ) ( #21922 , #21969 , #22007 , #22024 ) 
 
 
 Debloating wave — lighter installs, less you don't use — A clean pip install hermes-agent used to pull down everything: every messaging adapter SDK, every image-gen SDK, every voice/TTS provider, whether you used them or not. Now those heavy backends (Slack / Matrix / Feishu / DingTalk adapters, hindsight client, codex app-server, Pixverse / Camofox / image-gen SDKs, voice/TTS providers) install automatically the first time you actually use them. The [all] extras drop everything covered by lazy-deps, the installer falls back through tiers when a wheel doesn't fit your platform, and a supply-chain advisory checker scans every install for unsafe versions. Faster installs, smaller disk footprint, fewer transitive vulnerabilities. ( #24220 , #24515 , #25014 , #25038 , #25766 , #21818 ) 
 
 
 pip install hermes-agent &amp;&amp; hermes — Hermes Agent is now a real PyPI package. No more cloning the repo or running shell installers — one pip command and you're running. The wheel ships with the Ink TUI bundle and the shell launcher, so the full experience comes out of the box. (salvage of #26350 ) ( #26593 , #26148 ) 
 
 
 Cross-session 1h Claude prompt cache — When you use Claude through Anthropic, OpenRouter, or Nous Portal, the prompt prefix (system prompt, skills, memory) now caches for an hour across sessions. Start a /new session and the first response comes back faster and cheaper because the cache is still warm from your last session. Background memory review hits the cache too, so it's not paying full price every turn. ( #23828 , #25434 , #24778 ) 
 
 
 180x faster browser_console evaluations — When the agent uses the browser tool to inspect a page or run JavaScript, those calls now share one persistent connection to Chrome instead of spinning up a new DevTools session every time. The difference is huge: things that used to take a couple of seconds per call return in milliseconds. Real-world page interactions feel instant. ( #23226 ) 
 
 
 Cold-start performance wave — ~19 seconds off hermes launch — Running hermes used to make you wait through a chunk of import overhead and network calls before you saw a prompt. Now the launch path is mostly deferred: heavy adapters only load when you use them, model catalogs come from disk cache first, doctor checks run in parallel, and chat -q skips the welcome banner entirely. The hermes tools All-Platforms screen alone dropped from 14 seconds to under 1.5 seconds. ( #22138 , #22120 , #22681 , #22790 , #22808 , #22831 , #22859 , #22904 , #22766 , #25341 ) 
 
 
 Two new messaging platforms — LINE + SimpleX Chat — LINE is huge in Japan, Korea, and Taiwan, and now Hermes runs natively on the LINE Messaging API. SimpleX Chat is the privacy-focused decentralized messenger with no user IDs — also wired up as a first-class platform. That brings Hermes to 22 messaging platforms total, so wherever you and your team chat, the agent can be there. ( #23197 , #26232 ) 
 
 
 /handoff actually transfers the session live — Switching models or personalities mid-conversation used to mean losing context or starting over. Now /handoff moves your active session — every message, every tool call, every piece of context — to the target model, persona, or profile, live, without dropping anything. Mid-debugging hand off from a fast model to a deep-reasoning one, or pass a session between profiles for different parts of a task. ( #23395 ) 
 
 
 Native button UI for clarify on Telegram and Discord — When the agent uses the clarify tool to ask you a multiple-choice question, it now shows real platform-native buttons on Telegram and Discord instead of asking you to type back the option number. Tap the button, the agent gets your answer. Especially nice on mobile. ( #24199 , #25485 ) 
 
 
 Discord channel history backfill (default on) — When Hermes joins a Discord channel or thread for the first time, it now reads the recent message history so it knows what's been said before it responds. No more "what are we talking about?" — the agent has the context that's already on screen for everyone else. ( #25984 ) 
 
 
 vision_analyze returns pixels to vision-capable models — When you point the agent at an image with vision_analyze and the active model can actually see (GPT-5, Claude, Gemini, Grok-vision), Hermes now passes the raw pixels straight to the model instead of converting them to a text description first. You get the model's actual visual reasoning instead of a degraded text-summary round-trip. ( #22955 ) 
 
 
 Per-turn file-mutation verifier footer — After every turn that wrote or edited files, the agent now gets a short footer summarizing exactly what changed on disk — the file paths, the line counts, the actual delta. That means the agent catches its own mistakes when a write didn't land or got silently overwritten, instead of confidently telling you "I added the function" when the file wasn't actually saved. ( #24498 ) 
 
 
 LSP semantic diagnostics on every write — When the agent uses write_file or patch , Hermes now runs a real language server against the edited file and surfaces any new errors back to the agent before the next turn. Type errors, undefined symbols, missing imports — caught immediately. Goes way beyond v0.13.0's basic Python/JSON/YAML/TOML linting because it's actual semantic analysis. ( #24168 , #25978 ) 
 
 
 Unified video_generate with pluggable provider backends — One tool, any video model. Hermes ships with the obvious backends already, but you can drop in a new video provider as a plugin without touching core. So when a new video model lands next month, it can be a one-file plugin instead of a fork. ( #25126 ) 
 
 
 computer_use cua-driver backend — works with non-Anthropic models now — Computer-use (the agent controlling your mouse and keyboard to drive GUI apps) used to be locked to Anthropic's SDK. The new cua-driver backend works with non-Anthropic providers too, has proper focus-safe operations, and refreshes itself on hermes update . Now any vision-capable model can drive your desktop. (re-salvage of #16936 ) ( #21967 , #24063 ) 
 
 
 Clickable URLs in any terminal — Links in agent output are now real OSC8 hyperlinks with hover-highlight in any terminal that supports them. Click to open in your browser — no more copy-paste-trim of long URLs from the transcript. Just works in iTerm2, Kitty, Ghostty, modern Windows Terminal, etc. ( @OutThisLife ) ( #25071 , #24013 ) 
 
 
 Zed ACP Registry — uvx install in one click — Hermes is now listed in Zed's Agent Client Protocol registry, so Zed users can install it with one click. The install path uses uvx so there's no npm dependency. hermes acp --setup-browser bootstraps the browser tools for registry-driven installs. (salvage of #25908 ) ( #26079 , #26120 , #26234 ) 
 
 
 OpenRouter Pareto Code router with min_coding_score knob — OpenRouter's "Pareto" router automatically picks the cheapest model that meets a minimum quality bar. The new min_coding_score config lets you set that bar for coding tasks specifically — Hermes routes to the most affordable model that's at least that good at code. Stop paying for top-tier models when a mid-tier one would do. ( #22838 ) 
 
 
 NovitaAI as a new model provider — NovitaAI joins the provider lineup, giving you another option for open-source model hosting (Llama, Qwen, DeepSeek, etc.) with their pricing and rate limits. (salvage #7219 ) ( @kshitijk4poor ) ( #25507 ) 
 
 
 Codex app-server runtime for OpenAI/Codex models — An optional runtime that drives OpenAI's Codex CLI under the hood when you're using OpenAI or Codex paths. You get session reuse, automatic retirement of wedged sessions, and proper OAuth refresh classification — the kind of plumbing that makes long agentic runs not fall over. ( #24182 , #25769 ) 
 
 
 huggingface/skills as a trusted default tap — The community skills index hosted at huggingface.co/skills is now wired into the Skills Hub by default. So when somebody publishes a useful skill there, you can install it from your own hermes skills browser without any extra config. (closes #2549 ) ( #26219 ) 
 
 
 9 new optional skills — Hyperliquid (perp + spot trading via the SDK and REST API), Yahoo Finance (live market data, fundamentals, historicals), api-testing (REST + GraphQL debug recipes), unified EVM multi-chain (one skill covers Ethereum + L2s + Base), darwinian-ev

[... truncated for safety ...]