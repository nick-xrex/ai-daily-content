---
id: inbox_73626d0b
source: hermes-agent-releases
source_type: rss
url: "https://github.com/NousResearch/hermes-agent/releases/tag/v2026.6.19"
author: "teknium1"
published_at: 2026-06-19T19:40:43+00:00
fetched_at: 2026-06-19T22:00:26.948482+00:00
content_hash: "06dbb51c6a86dcda8bace2d757636c22256566c427699b3c22c57aa6944d72e9"
lang: en
caption_quality: None
raw: true
topics: []
---

# Hermes Agent v0.17.0 (v2026.6.19)

Hermes Agent v0.17.0 (v2026.6.19) 
 Release Date: June 19, 2026 
 Since v0.16.0: ~1,475 commits · ~800 merged PRs · 1,693 files changed · 235,390 insertions · 50,730 deletions · 300+ issues closed · 245 community contributors 
 
 The Reach Release. v0.16.0 put Hermes on your desktop. v0.17.0 is about how far that reach extends — across new places to talk to it, deeper into the tools you already use, and out to the people running Hermes for a team. Hermes reached two new channels (iMessage via Photon, and the Raft agent network), the desktop app gained substantial new capability, subagents can now run in the background, image generation learned to edit, and Cursor's Composer model is reachable through an xAI Grok subscription. The dashboard got a full profile builder and secure login, the Skills Hub browser was rehauled, the memory tool got a major upgrade, and the curator stopped spending aux-model budget on every routine run. 300+ issues closed ride along, plus a security round. 
 
 ✨ Highlights 
 
 
 Hermes reaches iMessage — Photon Spectrum, no Mac relay required — There's now an iMessage platform plugin built on Photon's managed line pool. Run hermes photon login , authenticate with a device code, and Hermes can send and receive iMessage — no Mac sitting in a closet running a relay, no BlueBubbles bridge to babysit. It's positioned as the successor to BlueBubbles: free to start, nothing to self-host. If your friends and family live in the blue bubbles, Hermes lives there now too. ( #32348 , #42582 , #44713 — @teknium1 ) 
 
 
 Raft — Hermes joins the Raft agent network as a gateway channel — A new bundled Raft platform adapter lets Hermes connect to Raft as an external agent through a wake-channel bridge. Set RAFT_PROFILE , run the bridge, and Raft can wake Hermes to handle messages — with a privacy-by-contract design where wake payloads carry only metadata (event IDs, timestamps), never message bodies. Another surface where Hermes can show up and do work. ( #48210 — @xxchan , @teknium1 ) 
 
 
 A substantially more capable desktop app — v0.16.0 shipped the desktop app; v0.17.0 deepened it across dozens of PRs. Rebindable keyboard shortcuts, native OS notifications with per-type toggles, live subagent watch-windows that stream a delegated agent's activity into its own pane, a composer model selector with per-model presets, automatic RTL/bidi text direction, a resizable VS Code-themed terminal pane, per-thread composer drafts, and the ability to install any VS Code Marketplace theme directly into the app. The desktop is now a serious daily driver, not a preview. ( #45866 , #40660 , #47060 , #46959 , #43292 , #44596 — @OutThisLife , @teknium1 ) 
 
 
 Background / async subagents — delegate work and keep going — delegate_task(background=true) now dispatches a subagent that runs in the background and returns a handle immediately. You and the model keep working while it churns, and the full result re-enters the conversation as a new turn the moment it finishes. Kick off a long research dive or a multi-step build, then carry on with something else instead of sitting blocked waiting on it. ( #40946 , #46968 — @teknium1 ) 
 
 
 Edit images, not just generate them — image-to-image in image_generate — image_generate can now edit and transform a source image, not only create one from scratch. Pass an existing image and a prompt and it routes to the backend's edit endpoint (same tool, same pattern as video_generate ), across every supported image provider. "Make this logo blue," "remove the background," "turn this sketch into a render" — all from the tool you already use. ( #48705 — @teknium1 ) 
 
 
 Automation Blueprints — schedule things without learning cron — Pick an automation by name and Hermes asks you for what it needs — no cron syntax, no slot=value typing. One blueprint definition renders natively on every surface: a form in the dashboard, a slash command in the CLI/TUI/messenger, a conversation with the agent, an entry in the docs catalog. "Daily news briefing at 8am" becomes a thing you set up by answering questions, not by memorizing 0 8 * * * . ( #41309 — @teknium1 ) 
 
 
 Cursor's Composer model, through your xAI Grok subscription — grok-composer-2.5-fast is now in the xAI OAuth model picker, with its context window reconciled to the full 200k. Composer is the fast coding model behind Cursor — and if you have an xAI Grok subscription, you can now point Hermes at it directly over OAuth, no separate API key. Your Grok plan, Hermes's agent loop, Composer's coding speed. ( #47908 , #6f89e17 — @teknium1 ) 
 
 
 Full profile builder in the dashboard — Build a complete Hermes profile from the browser — pick its model, choose its skills, attach its MCP servers — without hand-editing config.yaml . The dashboard also unified multi-profile management into one machine-wide view with a global profile switcher, so you manage every profile from a single place. ( #39084 , #44007 — @teknium1 ) 
 
 
 Skills Hub browser rehaul — The dashboard's Skills Hub got a ground-up rework: connected hubs, a Featured section, full skill previews before you install, and a security scan on each skill. Browsing and installing skills from the trusted taps (OpenAI, Anthropic, HuggingFace, NVIDIA) is now a real browsing experience, not a flat list. ( #40384 , #43398 — @teknium1 ) 
 
 
 The memory tool got a major upgrade — atomic batch operations — The memory tool gained an operations array that applies a batch of add/replace/remove edits atomically against the final character budget . The model can free up space and add new entries in a single call — even when an add alone would overflow the budget — collapsing what used to be a fragile multi-turn dance into one reliable operation. Memory updates are now faster and far less likely to fail mid-edit. ( #48507 — @teknium1 ) 
 
 
 Secure dashboard login — The dashboard's authentication was hardened: every token-required endpoint now correctly returns 401 behind the OAuth gate, websocket auth uses the served dashboard token, and a warning fires when a public_url override is silently rejected. Exposing your dashboard to the network is safer by default. ( #42578 , #42578 — @benbarclay , @teknium1 ) 
 
 
 Official WhatsApp Business Cloud API adapter — Alongside the existing Baileys bridge, Hermes now speaks the official WhatsApp Business Cloud API — Meta's first-party, hosted, no-bridge-process path. Point it at your Business API credentials and Hermes talks WhatsApp through the supported channel, with no QR-scanning bridge process to keep alive. ( #44331 , #43921 — @jquesnelle , @teknium1 ) 
 
 
 Rich text for Telegram — Bot API 10.1 rich messages — Telegram replies now render as proper rich messages via Bot API 10.1: better formatting, cleaner long-message handling, native markup instead of flattened text. It's on by default with an opt-out, so your Telegram conversations look the way they should without any configuration. ( #44829 , #45584 , #45953 — @teknium1 ) 
 
 
 Curator cost optimization — no aux-model spend on routine runs — The skill curator now prunes stale skills by default but no longer runs its LLM-powered consolidation pass unless you opt in ( curator.consolidate: true or hermes curator run --consolidate ). The deterministic inactivity sweep keeps running for free; the opinionated, aux-model-spending "build umbrella skills" fork is now off by default. Routine background curation costs you zero tokens . ( #47840 — @teknium1 ) 
 
 
 🖥️ Hermes Desktop App 
 New surfaces &amp; UX 
 
 Rebindable keyboard shortcuts panel; native OS notifications with per-type toggles; curated turn-completion cue + dismissable error banners ( #40660 , #45866 , #42480 , #47985 — @OutThisLife , @teknium1 ) 
 Live subagent watch-windows — stream a delegated agent's activity into its own pane; composer status stack + editable prompts; open any chat in its own window; new-session-in-compact-window hotkey ( #47060 , #44630 , #43219 , #46951 — @OutThisLife , @teknium1 ) 
 Composer model selector + per-model presets + external-provider disconnect; surface every provider/model from hermes model in the GUI; unify provider list to one source; warn when a main-model switch leaves auxiliary tasks pinned elsewhere ( #46959 , #40563 , #49080 , #40286 — @teknium1 , @OutThisLife ) 
 Install any VS Code Marketplace theme ; assignable themes per profile; window translucency slider; unified overlay design system + BrandMark + onboarding redesign ( #43292 , #42286 , #45086 , #40708 — @teknium1 , @OutThisLife ) 
 Resizable VS Code-themed terminal pane + palette polish; auto-detect RTL/bidi text direction in chat; Mac-style session switcher (^Tab / ^1-9); worktree-aware sidebar grouping; hover-reveal collapsed sidebars; messaging source folders in sidebar ( #42521 , #44596 , #43111 , #45273 , #41670 , #41751 — @OutThisLife ) 
 Arrow-key history + queue editing in composer; expand full command inline from the approval bar; follow-streaming-at-bottom + jump-to-bottom button; first-class cron jobs in the sidebar + dashboard scheduler ( #40234 , #44864 , #45263 , #40684 — @OutThisLife , @teknium1 ) 
 Desktop pets — pop-out overlay + notifications ( #47938 — @teknium1 ) 
 Full tool-backend config (pickers + per-backend settings) in Settings; run tool-backend post-setup installs from the GUI; uninstall the Chat GUI without removing the agent; Shift+click status-bar zap to toggle YOLO globally; /browser connect on a local gateway ( #41232 , #40559 , #40355 , #41666 , #47245 — @teknium1 , @OutThisLife ) 
 Japanese + Traditional Chinese language switching ( #40114 ) 
 "Restart gateway" action (renamed from "Restart messaging") surfaced in the statusbar + on messaging save/toggle toasts; rendered logs are selectable/copyable ( #49094 — @OutThisLife ) 
 
 Remote-gateway &amp; multi-profile 
 
 Remote media relay — attach images/PDFs and display agent-written images over the network for the first time; remote-gateway file attachments via file.attach ( #41336 , #42634 — @teknium1 ) 
 Client + backend version buttons + remote-backend update flow; browse remote backend files; route global-remote profile REST calls; recover chat after sleep/wake by revalidating a stale remote backend ( #42181 , #44326 , #47011 , #41350 — @OutThisLife , @teknium1 ) 
 Multi-profile fallout cleanup — WS auth + cross-profile session reads; release profile backends before delete; scope session list/model switch/timer per session ( #44529 , #42613 , #41103 , #41120 , #41182 — @OutThisLife , @teknium1 ) 
 Stream subagent activity into watch windows; keep streaming painting in unfocused secondary chat windows; recover stranded session windows ( #47060 , #47919 , #47655 — @OutThisLife ) 
 
 📊 Web Dashboard 
 
 Full-featured profile builder (model + skills + MCPs); unify multi-profile management — one machine dashboard + global profile switcher; profile-scoped skills &amp; toolsets; session switcher panel on the Chat tab ( #39084 , #44007 , #43808 , #49077 — @teknium1 ) 
 Skills hub browser rehaul — connected hubs, featured, preview + security scan; SKILL.md editor on Skills page + attach-skill selector in cron modals; full per-MCP catalog detail; full tool-backend config in the GUI ( #40384 , #44231 , #48520 , #40418 — @teknium1 ) 
 Enable webhooks from the Webhooks page; idempotent hermes dashboard register ; auto-restart gateway after Telegram QR onboarding; file browser; change UI font from the theme picker; reasoning-effort picker in the chat sidebar ( #44021 , #42455 , #43424 , #43512 , #41145 , #49141 — @teknium1 ) 
 
 🏗️ Core Agent &amp; Architecture 
 God-file refactor wave (run_agent.py / cli.py / gateway/run.py) 
 
 cli.py main() 3297 → 954 lines — extracted 28 subcommand parsers into hermes_cli/subcommands/ , then promoted 9 closure handlers; 32 slash-command handlers → CLICommandsMixin ; 18 model-flow wizard functions → model_setup_flows ; agent-construction cluster → CLIAgentSetupMixin ( #41798 , #41835 , #41942 , #4

[... truncated for safety ...]