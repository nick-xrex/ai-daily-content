---
id: inbox_eee8083e
source: hermes-agent-releases
source_type: rss
url: "https://github.com/NousResearch/hermes-agent/releases/tag/v2026.5.7"
author: "teknium1"
published_at: 2026-05-07T16:23:08+00:00
fetched_at: 2026-05-22T18:00:31.392404+00:00
content_hash: "7756b8eeac9d3aebf95f0162d42afd35270bab716f778e2b92885a056a77a5ea"
lang: en
caption_quality: None
raw: true
topics: []
---

# Hermes Agent v0.13.0 (2026.5.7) — The Tenacity Release

Hermes Agent v0.13.0 (v2026.5.7) 
 Release Date: May 7, 2026 
 Since v0.12.0: 864 commits · 588 merged PRs · 829 files changed · 128,366 insertions · 282 issues closed (13 P0, 36 P1) · 295 community contributors (including co-authors) 
 
 The Tenacity Release — Hermes Agent now finishes what it starts. Kanban ships as a durable multi-agent board (heartbeat, reclaim, zombie detection, auto-block on incomplete exit, per-task retries, hallucination recovery). /goal keeps the agent locked on a target across turns (Ralph loop). Checkpoints v2 rewrites state persistence with real pruning. Gateway auto-resumes interrupted sessions after restart. Cron grows a no_agent watchdog mode. A security wave closes 8 P0s — redaction is now ON by default, Discord role-allowlists are guild-scoped, WhatsApp rejects strangers by default, and TOCTOU windows close across auth.json and MCP OAuth. Google Chat becomes the 20th platform. Providers become a pluggable surface. Seven i18n locales ship. 
 
 
 ✨ Highlights 
 
 
 Multi-agent Kanban — delegate to an AI team that actually finishes — Spin up a durable board, drop tasks on it, and let multiple Hermes workers pick them up, hand off, and close them out. Heartbeats, reclaim, zombie detection, retry budgets, and a hallucination gate keep the team honest. One install, many kanbans. ( #17805 , #19653 , #20232 , #20332 , #21330 , #21183 , #21214 ) 
 
 
 /goal — the agent doesn't forget what you asked it to do — Lock the agent onto a target and it stays on task across turns. The Ralph loop as a first-class primitive. ( #18262 , #18275 , #21287 ) 
 
 
 Show it a video — new video_analyze tool for native video understanding on Gemini and compatible multimodal models. ( @alt-glitch ) ( #19301 ) 
 
 
 Clone a voice — xAI Custom Voices lands as a TTS provider with voice cloning support. ( @alt-glitch ) ( #18776 ) 
 
 
 Hermes speaks your language — static gateway + CLI messages translate to 7 locales: Chinese, Japanese, German, Spanish, French, Ukrainian, and Turkish. Docs site gains a Chinese (zh-Hans) locale. ( #20231 , #20329 , #20467 , #20474 , #20430 , #20431 ) 
 
 
 Google Chat — the 20th messaging platform — plus a generic platform-plugin hooks surface so third-party adapters drop in without touching core (IRC and Teams migrated). ( #21306 , #21331 ) 
 
 
 Sessions survive restarts — gateway bounces mid-agent, /update restarts, source-file reloads — conversations auto-resume when the gateway comes back. ( #21192 ) 
 
 
 Security wave — 8 P0 closures — redaction ON by default, Discord role-allowlists guild-scoped (CVSS 8.1 cross-guild DM bypass closed), WhatsApp rejects strangers by default, TOCTOU windows closed across auth.json and MCP OAuth, browser enforces cloud-metadata SSRF floor, cron prompt-injection scans assembled skill content, hermes debug share redacts at upload. ( #21193 , #21241 , #21291 , #21176 , #21194 , #21228 , #21350 , #19318 ) 
 
 
 Checkpoints v2 — state persistence rewritten. Real pruning, disk guardrails, no more orphan shadow repos. ( #20709 ) 
 
 
 The agent lints its own writes — post-write delta lint on write_file + patch . Python, JSON, YAML, TOML. Syntax errors surface immediately instead of shipping downstream. ( #20191 ) 
 
 
 no_agent cron mode — script-only watchdog — cron jobs can now skip the agent entirely and just run a script. Empty stdout is silent, non-empty gets delivered verbatim. ( #19709 ) 
 
 
 Platform allowlists everywhere — allowed_channels / allowed_chats / allowed_rooms config across Slack, Telegram, Mattermost, Matrix, and DingTalk. ( #21251 ) 
 
 
 Providers are now plugins — ProviderProfile ABC + plugins/model-providers/ . Drop in third-party providers without touching core. ( #20324 ) 
 
 
 API server — long-term memory per session — X-Hermes-Session-Key header gives memory providers a stable session identifier. ( #20199 ) 
 
 
 MCP levels up — SSE transport with OAuth forwarding, stale-pipe retries, image results surface as MEDIA tags instead of getting dropped, keepalive on long-lived lifecycle waits. ( #21227 , #21323 , #21289 , #21328 , #20209 ) 
 
 
 Curator grows subcommands — hermes curator archive , prune , list-archived . Manual hermes curator run is synchronous now — you see results without polling. ( #20200 , #21236 , #21216 ) 
 
 
 ACP — /steer and /queue — direct the in-flight agent or queue follow-ups from Zed, VS Code, or JetBrains. Plus atomic session persistence and reasoning-metadata preservation across restarts. ( @HenkDz ) ( #18114 , #20279 , #20296 , #20433 ) 
 
 
 TUI glow-up — /model picker matches hermes model with inline auth ( @austinpickett ), collapsible startup banner sections ( @kshitijk4poor ), context-compression counter in the status bar. ( #18117 , #20625 , #21218 ) 
 
 
 Dashboard grows up — Plugins page (manage, enable/disable, auth status) ( @austinpickett ), Profiles management page ( @vincez-hms-coder ), sortable analytics tables, reverse-proxy support via X-Forwarded-Prefix , new default-large 18px theme. ( #18095 , #16419 , #18192 , #21296 , #20820 ) 
 
 
 SearXNG + split web tools — SearXNG ships as a native search-only backend; web tools now let you pick different backends per capability (search vs extract vs browse). ( @kshitijk4poor ) ( #20823 , #20061 , #20841 ) 
 
 
 OpenRouter response caching — explicit cache control for models that expose it. ( @kshitijk4poor ) ( #19132 ) 
 
 
 [[as_document]] — skill media-routing directive — skills can force the gateway to deliver output as a document on platforms that support it. ( #21210 ) 
 
 
 transform_llm_output plugin hook — new lifecycle hook that lets plugins reshape or filter LLM output before it hits the conversation. Useful for context-window reducers and content filters. ( #21235 ) 
 
 
 Nous OAuth persists across profiles — shared token store: sign in once, every profile inherits the session. ( #19712 ) 
 
 
 QQBot — native approval keyboards — feature parity with Telegram / Discord approval UX. Chunked upload, quoted attachments. ( #21342 , #21353 ) 
 
 
 6 new optional skills — Shopify (Admin + Storefront GraphQL), here.now, shop-app personal shopping assistant, Anthropic financial-services bundle, kanban-video-orchestrator ( @SHL0MS ), searxng-search ( @kshitijk4poor ). ( #18116 , #18170 , #20702 , #21180 , #19281 , #20841 ) 
 
 
 New models — deepseek/deepseek-v4-pro , x-ai/grok-4.3 , openrouter/owl-alpha (free), tencent/hy3-preview ( @Contentment003111 ), Arcee Trinity Large Thinking temperature + compression overrides. ( #20495 , #20497 , #18071 , #21077 , #20473 ) 
 
 
 100 fresh CLI startup tips — the random tip banner gets 100 new entries covering cron, kanban, curator, plugins, and lesser-known flags. ( #20168 ) 
 
 
 
 🧩 Multi-Agent Kanban (Durable) 
 New — durable multi-profile collaboration board 
 
 feat(kanban): durable multi-profile collaboration board — post-revert reimplementation, multi-profile by design ( #17805 ) 
 Multi-project boards — one install, many kanbans ( #19653 , #19679 ) 
 Share board, workspaces, and worker logs across profiles ( #19378 ) 
 Hallucination gate + recovery UX for worker-created-card claims (closes #20017 ) ( #20232 ) 
 Generic diagnostics engine for task distress signals ( #20332 ) 
 Per-task max_retries override (supersedes #20972 ) ( #21330 ) 
 Multiline textarea for inline-create title (salvage of #20970 ) ( #21243 ) 
 
 Kanban Dashboard 
 
 Workspace kind + path inputs in inline create form ( #19679 ) 
 Per-platform home-channel notification toggles ( #19864 ) 
 Sharper home-channel toggle contrast + drop → running action ( #19916 ) 
 Fix: reject direct status transition to 'running' via dashboard API (salvage of #19554 ) ( #19705 ) 
 Fix: dashboard board pin authoritative over server current file ( #20879 ) ( #21230 ) 
 Fix: treat dashboard event-stream cancellation as normal shutdown ( #20790 ) ( #21222 ) 
 Fix: filter dashboard board by selected tenant ( #19817 ) ( #21349 ) 
 Fix: code/pre styling theme-immune across all themes ( #21086 ) ( #21247 ) 
 Fix: reset &lt;code&gt; background inside dashboard board ( #20687 ) 
 Fix: preserve dashboard completion summaries + add kanban edit (salvages #20016 ) ( #20195 ) 
 Fix: avoid fragile failure-column renames (salvage #20848 ) ( @kshitijk4poor ) ( #20855 ) 
 
 Worker lifecycle + reliability 
 
 Heartbeat + reclaim + zombie + retry-cap fixes ( #21147 , #21141 , #21169 , #20881 ) ( #21183 ) 
 Auto-block workers that exit without completing + shutdown race ( #20894 ) ( #21214 ) 
 Detect darwin zombie workers (salvages #20023 ) ( #20188 ) 
 Unify failure counter across spawn/timeout/crash outcomes ( #20410 ) 
 Enforce worker task-ownership on destructive tool calls ( #19713 ) 
 Drop worker identity claim from KANBAN_GUIDANCE ( #19427 ) 
 Fix: skip dispatch for tasks assigned to non-profile lanes (salvages #20105 , #20134 ) ( #20165 ) 
 Fix: include default profile in on-disk assignee enumeration (salvages #20123 ) ( #20170 ) 
 Fix: ignore stale current board pointers (salvages #20063 ) ( #20183 ) 
 Fix: profile discovery ignores HERMES_HOME in custom-root deployments ( @jackey8616 ) ( #19020 ) 
 Fix: allow orchestrator profiles to see kanban tools via toolsets config ( #19606 ) 
 
 Batch salvages 
 
 Tier-1 batch — metadata test, max_spawn config, run-id lifecycle guard (salvages #19522 #19556 #19829 ) ( #20440 ) 
 Tier-2 batch — doctor, started_at, parent-guard, latest_summary, selects, linked-children ( #20448 ) 
 
 Documentation 
 
 Backfill multi-board refs in reference docs ( #19704 ) 
 Document /kanban slash command ( #19584 ) 
 Document recommended handoff evidence metadata (salvage #19512 ) ( #20415 ) 
 Fix orchestrator + worker skill setup instructions ( @helix4u ) ( #20958 , #20960 ) 
 
 
 🎯 Persistent Goals, Checkpoints &amp; Session Durability 
 /goal — persistent cross-turn goals (Ralph loop) 
 
 feat: /goal — persistent cross-turn goals ( #18262 ) 
 Docs page — Persistent Goals (/goal) ( #18275 ) 
 Fix: honor configured goal turn budget (salvage #19423 ) ( #21287 ) 
 
 Checkpoints v2 
 
 Single-store rewrite with real pruning + disk guardrails ( #20709 ) 
 
 Session durability 
 
 Auto-resume interrupted sessions after gateway restart (salvage #20888 ) ( #21192 ) 
 Preserve pending update prompts across restarts ( #20160 ) 
 Preserve home-channel thread targets across restart notifications (salvage #18440 ) ( #19271 ) 
 Preserve thread routing from cached live session sources ( #21206 ) 
 Preserve assistant metadata when branching sessions ( #18222 ) 
 Preserve thread routing for /update progress and prompts ( #18193 ) 
 Preserve document type when merging queued events ( #18215 ) 
 
 
 🛡️ Security &amp; Reliability 
 Security hardening (8 P0 closures) 
 
 Enable secret redaction by default ( #17691 , #20785 ) ( #21193 ) 
 Discord — scope DISCORD_ALLOWED_ROLES to originating guild ( #12136 , CVSS 8.1) ( #21241 ) 
 WhatsApp — reject strangers by default, never respond in self-chat ( #8389 ) ( #21291 ) 
 MCP OAuth — close TOCTOU window when saving credentials ( #21176 ) 
 hermes_cli/auth.py — close TOCTOU window in credential writers ( #21194 ) 
 Browser — enforce cloud-metadata SSRF floor in hybrid routing ( #16234 ) ( #21228 ) 
 hermes debug share — redact log content at upload time ( @GodsBoy ) ( #19318 ) 
 Cron — scan assembled prompt including skill content for prompt injection ( #3968 ) ( #21350 ) 
 Restore .env/auth.json/state.db with 0600 perms ( #19699 ) 
 SRI integrity for dashboard plugin scripts (salvage #19389 ) ( #21277 ) 
 Bind Meet node server to localhost, restrict token file to owner read ( #19597 ) 
 Extend sensitive-write target to cover shell RC and credential files ( #19282 ) 
 Harden YOLO mode env parsing against quoted-bool strings ( #18214 ) 
 OSV-Scanner CI + Dependabot for github-actions only ( #20037 ) 
 
 Reliability — critical bug closures 
 
 CLI crash on startup — Invalid key 'c-S-c' (P0, prompt_toolkit doesn't support Shift modifier) ( #19895 , #19919 )

[... truncated for safety ...]