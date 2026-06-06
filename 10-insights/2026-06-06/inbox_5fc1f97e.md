---
id: inbox_5fc1f97e
date: 2026-06-06
source_ref: "[[00-inbox/2026-06-06/0215-hermes-agent-releases-hermes-agent-v0-16-0-2026-6-5-the-surfac-13d4]]"
title: "Hermes Agent v0.16.0 (2026.6.5) — The Surface Release"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.6.5
source: hermes-agent-releases
published_at: 2026-06-06T00:57:25+00:00
fetched_at: 2026-06-06T02:20:47.094530+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent v0.16.0 (The Surface Release) 推出全新原生桌面應用，支援 macOS/Linux/Windows 一鍵安裝、拖放檔案、狀態列模型選擇、自動更新。新增遠端 Hermes gateway 連接，桌面 GUI 可透過 OAuth/帳密連接遠端伺服器，支援多設定檔並行工作階段。Web 管理面板升級為完整後台，支援 MCP 目錄、訊息頻道配置（Telegram/Discord/Slack）、認證、webhook 等，無需 SSH 編輯設定。模型選擇器全面模糊搜尋，skills 集合精簡為實際需求，NVIDIA 成為信任供應商，新增 /undo [N] 命令，提供簡體中文完整翻譯。本次發布涵蓋 874 commits、542 個合併 PR、修復 399 個 issue（含 2 P0、62 P1、16 安全標籤）。"
key_points:
  - "推出原生桌面應用（Electron），支援 macOS/Linux/Windows，一鍵安裝、拖放檔案、狀態列模型選擇、命令調色盤等本地應用功能"
  - "新增遠端 Hermes gateway 連接（OAuth/帳密認證），計算和 UI 分離，桌面應用指向遠端伺服器，支援多設定檔並行工作階段"
  - "Web 管理面板完整化：MCP 目錄管理、訊息頻道配置、認證管理、webhook 建立，免除 SSH 操作，降低部署複雜度"
tags: [hermes-agent, desktop-app, native-ui, remote-gateway, admin-panel, chinese-localization]
topics: [agents.mcp]
importance: 5
novelty: 5
insight_quality: 3
insight_type: announcement
deep_dive_candidate: true
deep_dive_approved: false
---

## Hermes Agent v0.16.0 (2026.6.5) — The Surface Release

Hermes Agent v0.16.0 (The Surface Release) 推出全新原生桌面應用，支援 macOS/Linux/Windows 一鍵安裝、拖放檔案、狀態列模型選擇、自動更新。新增遠端 Hermes gateway 連接，桌面 GUI 可透過 OAuth/帳密連接遠端伺服器，支援多設定檔並行工作階段。Web 管理面板升級為完整後台，支援 MCP 目錄、訊息頻道配置（Telegram/Discord/Slack）、認證、webhook 等，無需 SSH 編輯設定。模型選擇器全面模糊搜尋，skills 集合精簡為實際需求，NVIDIA 成為信任供應商，新增 /undo [N] 命令，提供簡體中文完整翻譯。本次發布涵蓋 874 commits、542 個合併 PR、修復 399 個 issue（含 2 P0、62 P1、16 安全標籤）。

### 重點
- 推出原生桌面應用（Electron），支援 macOS/Linux/Windows，一鍵安裝、拖放檔案、狀態列模型選擇、命令調色盤等本地應用功能
- 新增遠端 Hermes gateway 連接（OAuth/帳密認證），計算和 UI 分離，桌面應用指向遠端伺服器，支援多設定檔並行工作階段
- Web 管理面板完整化：MCP 目錄管理、訊息頻道配置、認證管理、webhook 建立，免除 SSH 操作，降低部署複雜度

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v2026.6.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.16.0 (v2026.6.5) 
 Release Date: June 5, 2026 
 Since v0.15.2: 874 commits · 542 merged PRs · 1,962 files changed · 205,216 insertions · 46,217 deletions · 399 issues closed (2 P0, 62 P1, 16 security-tagged) · 170 community contributors (including co-authors) 
 
 The Surface Release. Hermes meets you wherever you work. A brand-new native desktop app — built across 100 PRs and 159 commits in a single week — gives you Hermes as a real macOS/Linux/Windows application: one-click install, in-app self-update, drag-and-drop files into chat, an inline model picker in the status bar, concurrent multi-profile sessions, a full Simplified Chinese translation, and the ability to connect to a remote Hermes gateway over OAuth or username/password. Alongside it, the web dashboard grew a full browser-based administration panel (MCP catalog, messaging channels, credentials, webhooks, memory, pluggable OIDC / username-password login), and first-time setup got a "Quick Setup via Nous Portal" path that gets you from install to first message in seconds. The default skill set was trimmed to what you actually need, NVIDIA/skills joined the trusted Skills Hub taps, the model picker is now fuzzy-searchable everywhere (desktop, web, TUI, CLI), and /undo finally lets you take back the last N turns. 2 P0 and 62 P1 closures ride along, plus a security round (CVE-2026-48710 Starlette pin, SSRF off-loop hardening, subprocess credential stripping). 
 
 
 ✨ Highlights 
 
 
 Hermes Desktop — a real native app, not a terminal wrapper — This is the headline. There's now a apps/desktop/ Electron application that installs like any other desktop app on macOS, Linux, and Windows, updates itself in place from inside the app, and gives you a polished GUI for everything Hermes does. You get a proper chat window with streaming, a session list you can archive and search, drag-and-drop files anywhere in the chat area, clipboard image paste, a Cmd+K command palette, and a model picker right in the status bar. If you've been telling friends "it's a CLI agent" and watching their eyes glaze over — now you can just send them an installer. None of this existed a week ago. ( #20059 , #35607 , #37099 , #37379 , #38631 — @OutThisLife , @jquesnelle , @ethernet8023 , @austinpickett , @benbarclay ) 
 
 
 Run the desktop app against a remote Hermes — sign in with OAuth or username/password — The desktop app doesn't have to run Hermes locally. Point it at a remote Hermes gateway (your homelab, a hosted box, a teammate's server) and it connects over a secure WebSocket, authenticating with OAuth or a username/password login — no fiddling with --insecure flags or hand-copied session tokens. Each profile can target its own remote host, and you can run concurrent sessions across multiple profiles in one window with cross-profile @session links. The practical version: your laptop runs a thin GUI, the heavy agent runs wherever your API keys and compute live. ( #37888 , #38851 , #39330 , #39778 — @benbarclay , @OutThisLife , @teknium1 ) 
 
 
 The web dashboard is now a full admin panel — configure everything from the browser — The dashboard grew from "view your sessions" into a complete administration surface. There's a Channels page that sets up every gateway messaging platform (Telegram, Discord, Slack, etc.) from the browser, an admin panel for the MCP catalog with enable/disable toggles, credential management, webhook and hook creation, memory configuration, gateway controls, and a System page with check-before-update and one-click Debug Share. You no longer have to SSH in and edit config.yaml to wire up a new messaging channel or MCP server — it's all point-and-click now. ( #36704 , #36736 , #37211 , #38205 , #38600 — @teknium1 ) 
 
 
 Hermes Desktop speaks Simplified Chinese — full 简体中文 in the chat GUI — The desktop app now ships a complete Simplified Chinese (简体中文) translation across every UI surface — the chat window itself, sidebar, settings, command center, cron, messaging, profiles, skills, agents, the lot. English stays the default; switch language in Appearance settings and the choice persists to your config ( display.language ). It's built on a proper typed i18n layer, so adding more languages from here is straightforward. ( #38241 — @JimLiu ) 
 
 
 Leaner default skill set — Hermes ships only what you actually need — The bundled skill set got a deliberate trim. Skills that were redundant or dead are gone ( spotify — superseded by the native Spotify plugin's 7 tools; linear — superseded by hermes mcp install linear ; kanban-codex-lane , debugging-hermes-tui-commands , a stale domain orphan, and several empty category markers). Heavier or niche skills moved from bundled to optional (the Baoyu creative set, dspy , subagent-driven-development , minecraft-modpack-server , pokemon-player , hermes-s6-container-supervision ) — still one hermes skills install away, just not loaded by default. And a new environments: relevance gate keeps context-specific skills (kanban, docker/s6) out of the skills index for users who'll never use them, while still loading them on explicit request. The result: a smaller, sharper default skill list, less noise in the picker, and a lighter prompt. The curator can now prune unused built-in skills too (not just agent-created ones), with usage tracked for every skill. ( #39028 , #36701 , #36228 — @teknium1 ) 
 
 
 NVIDIA/skills is now a built-in trusted skills tap — NVIDIA/skills joins OpenAI, Anthropic, and HuggingFace as a default trusted tap in the Skills Hub — discoverable, browsable, searchable, and auto-updating through the same pipeline. NVIDIA's verified skills for CUDA-X, AIQ, cuOpt and the rest of their product stack are one install away, with real category labels from the repo's skills.sh.json sidecar. ( #34333 — @teknium1 ) 
 
 
 Quick Setup via Nous Portal — from install to first message in seconds — First-time setup was thinned down to two clear paths: Quick Setup (sign in with Nous Portal, get a model picker, start chatting immediately) or Full Setup (the detailed wizard for power users). hermes portal is now the human-readable alias that runs the full quick-setup Nous flow. The first-run menu explains the difference inline so newcomers aren't guessing. The goal: a brand-new user shouldn't need to read docs to send their first message. ( #35723 , #36227 , #38449 , #38465 — @teknium1 , @kshitijk4poor ) 
 
 
 Fuzzy model picker, everywhere — type a few letters, find your model — The model picker now does fuzzy search across the desktop app, web dashboard, TUI, and CLI. Type "v4fl" and deepseek-v4-flash surfaces; multi-endpoint providers are grouped under one row instead of cluttering the list with duplicates, and each row carries a description so you know what you're picking. The catalog refreshes hourly instead of daily, so new models show up the same day they launch. New this window: deepseek-v4-flash , MiniMax-M3 with 1M context, qwen3.7-plus . ( #36928 , #35227 , #35756 , #35659 , #36214 — @kshitijk4poor , @teknium1 ) 
 
 
 /undo [N] — take back the last N turns — Said the wrong thing, or sent the agent down a bad path? /undo backs up N user turns, prefills your last message so you can edit and resend, and soft-deletes the turns in between. It works in the CLI, the TUI, and across messaging platforms (Telegram, Discord, etc.) with full parity. Closes a long-standing request ( #21910 ). ( #36229 , #36699 — @teknium1 ) 
 
 
 Choose your default interface — cli or tui — You can now set whether hermes chat drops you into the classic CLI or the Ink TUI by default, with a --cli flag to override per-invocation. The TUI also got a single unified /model command and a Sessions overlay for switching between live sessions. Use the interface you actually like. ( #37782 , #37112 — @OutThisLife ) 
 
 
 
 🖥️ Hermes Desktop App (NEW) 
 Install &amp; lifecycle 
 
 macOS desktop install + in-app self-update; rebuild-and-relaunch cleanly on macOS ( #35607 , #36198 , #38296 — @OutThisLife ) 
 macOS installer renamed to "Hermes" and turned into a launcher ( #37516 — @OutThisLife ) 
 Build desktop in its own desktop stage on macOS/Linux instead of silently skipping; content-hash build stamp, --build-only / --force-build flags ( #36134 — @OutThisLife , #37597 — @ethernet8023 ) 
 Boot-failure recovery + live API-key validation; cancellable install; recover from corrupt cached Electron download ( #35864 , #37379 , #39032 — @OutThisLife , @teknium1 ) 
 Windows: recover from corrupt Electron cache in bootstrap install; stop racing our own backend during in-app update ( #39465 , #39828 — @teknium1 , @OutThisLife ) 
 Linux: configure Electron sandbox helper; detect linux arm64 binary; disable GPU acceleration on remote displays to stop flicker ( #37691 , #38594 , #37932 — @ethernet8023 , @OutThisLife ) 
 Require Node ≥20.19/22.12 for the desktop build; zero eslint/typecheck debt + prettier pass ( #38255 , #39100 — @OutThisLife ) 
 
 Remote-gateway &amp; multi-profile 
 
 Connect to OAuth-gated remote gateways; username/password login for remote gateways; per-profile remote gateway hosts ( #37888 , #38851 , #39778 — @benbarclay , @teknium1 , @OutThisLife ) 
 Concurrent multi-profile sessions, cross-profile @session links; re-mint OAuth WS ticket on gateway reconnect; gate OAuth remote connect on AT-or-RT ( #39330 , #38886 , #39464 — @OutThisLife , @teknium1 , @benbarclay ) 
 Offer remote sign-in on a gated-gateway boot failure; validate live WebSocket in remote gateway test ( #39402 , #39511 — @teknium1 ) 
 
 Chat UX &amp; settings 
 
 Drop files anywhere in the chat area; clipboard image paste with dedupe; attachments on Enter, IME composition handling ( #36262 , #38306 , #38677 — @OutThisLife , @teknium1 ) 
 Background needs-input indicator, clarify redesign, Cmd+K palette &amp; UI consistency pass; inline model picker in the status bar; YOLO toggle in the status bar (TUI parity) ( #38631 , #37738 , #38517 — @OutThisLife ) 
 Session-list overhaul, session hygiene/archive, media streaming + connecting overlay; search sessions by id (SQL-bounded) ( #37379 , #37099 , #39062 — @OutThisLife , @teknium1 ) 
 Dedicated Providers settings + polished Accounts/API-keys UX; consolidate skills + tools management into one pane; move model management into Settings ( #38551 — @austinpickett , #37310 , #37330 — @jquesnelle ) 
 Render approval/sudo/secret prompts so tools stop silently timing out; surface skill &amp; quick-command slash commands in the palette; first-class xAI Grok OAuth provider in the launcher ( #38578 , #38531 , #37697 — @teknium1 , @OutThisLife ) 
 "Choose provider later" skip on first-run onboarding; onboarding can configure a local/custom endpoint without an API key; custom zoom shortcuts ( #39483 , #38572 , #37894 — @teknium1 , @ethernet8023 ) 
 macOS helper microphone entitlement; scroll-jump fixes (native anchoring, at-rest jump, wheel-up snap-back); thinking block stays open mid-streaming ( #37745 — @xxxigm , #37866 , #38221 , #38809 — @OutThisLife , @teknium1 , @stremtec ) 
 GUI quality-of-life triage batch; salvaged AhmetArif0 desktop/dashboard fixes; rename session via session.title RPC so /title works ( #37536 — @austinpickett , #39070 , #39410 — @teknium1 , @benbarclay ) 
 hermes debug share / /debug / hermes logs now include desktop.log ( #38203 — @teknium1 ) 
 Simplified Chinese (简体中文) translation across every desktop UI surface — typed i18n layer, switch in Appearance settings, persisted via display.language (English remains default) ( #38241 — @JimLiu ) 
 Full multi-profile support over one global-remote dashboard; remote-profile sessions are first-class (resume, read, rename/archive/delete); new chats honor their profile in global-remote mode ( #39921 , #39894 , #39993 — @OutThisLife ) 
 
 📊 Web Dashboard 
 Administration panel (NEW) 
 
 Full administration panel — MCP catalog with enable/disable toggles, pairing, webhooks, credentials, memory, gateway, hook creation, system settin

[... truncated for safety ...]

</details>