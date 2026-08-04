---
id: inbox_4a5cd795
date: 2026-08-03
source_ref: "[[00-inbox/.../inbox_4a5cd795]]"
title: "Hermes Agent v0.20.0 (2026.8.3)"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.3
source: hermes-agent-releases
published_at: 2026-08-03T16:57:52+00:00
fetched_at: 2026-08-04T01:52:41.984935+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent v0.20.0「Herald Release」整合了 3,650 次提交、1,400 個合併 PR，關閉 1,200 個議題。核心創新涵蓋實時流式語音對話搭配中斷能力（barge-in）與忙碌感知靜默檢測，開放詞彙喚醒詞與跨平台語音支援（WhatsApp、Feishu、DingTalk、LINE、QQ 等）。代理間通訊協議 A2A v1.0 實現異構代理棧間標準通訊，關閉長期功能請求 #514；工具自我修復機制將迭代限制從 90 擴展至 500，大幅減少長期自主執行中斷。桌面應用升級為平台，支援製品預覽、外掛 SDK、全局快捷鍵；CLI 新增 !command、/init、/diff、/context、/focus 等命令；上下文壓縮與驗證型引用機制使長會話保持連貫。"
key_points:
  - "A2A v1.0 協議實現代理間通訊標準，迭代限制從 90 擴至 500 減少自主任務中斷"
  - "實時流式語音 + 中斷能力、開放詞彙喚醒詞、跨 8+ 平台多語言 STT/TTS"
  - "桌面平台化（製品預覽、外掛 SDK）與 CLI 增強（!command、/diff、/context、/focus）"
tags: [real-time-voice, agent-to-agent, tool-recovery, context-compression, grounded-citations]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.20.0 (2026.8.3)

Hermes Agent v0.20.0「Herald Release」整合了 3,650 次提交、1,400 個合併 PR，關閉 1,200 個議題。核心創新涵蓋實時流式語音對話搭配中斷能力（barge-in）與忙碌感知靜默檢測，開放詞彙喚醒詞與跨平台語音支援（WhatsApp、Feishu、DingTalk、LINE、QQ 等）。代理間通訊協議 A2A v1.0 實現異構代理棧間標準通訊，關閉長期功能請求 #514；工具自我修復機制將迭代限制從 90 擴展至 500，大幅減少長期自主執行中斷。桌面應用升級為平台，支援製品預覽、外掛 SDK、全局快捷鍵；CLI 新增 !command、/init、/diff、/context、/focus 等命令；上下文壓縮與驗證型引用機制使長會話保持連貫。

### 重點
- A2A v1.0 協議實現代理間通訊標準，迭代限制從 90 擴至 500 減少自主任務中斷
- 實時流式語音 + 中斷能力、開放詞彙喚醒詞、跨 8+ 平台多語言 STT/TTS
- 桌面平台化（製品預覽、外掛 SDK）與 CLI 增強（!command、/diff、/context、/focus）

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Hermes Agent v0.20.0 (2026.8.3)

Hermes Agent v0.20.0 (v2026.8.3) 
 Release Date: August 3, 2026 
 Since v0.19.0: ~3,650 commits · ~1,400 merged PRs · ~5,200 files changed · ~559,000 insertions · ~405,000 deletions · ~1,200 issues closed · 650+ contributors 
 
 The Herald Release. Hermes is the herald of the gods, and this release makes him one in earnest: he speaks (real-time conversational voice with streaming TTS, barge-in, on-device wake words, and hands-free control across the CLI, desktop, and every audio-capable gateway platform), he carries word to other agents (A2A v1.0), he announces events to your systems (signed outbound webhooks), and he cites his sources (grounded research with verifiable citations and fact-checking). Around that spine: the desktop app became a platform (artifacts with live preview, a plugin SDK, quick-entry from anywhere, multiple windows), the CLI got a wave of power commands ( ! shell mode, /init , /diff , /context , /focus ), compression got smarter and gentler, and the tools themselves now recover from their own failures instead of making the model guess. This release rolls up everything from the v0.19.1 infrastructure patch tag — that window is fully documented here. 
 
 
 ✨ Highlights 
 
 
 Talk to Hermes — streaming, conversational voice with barge-in — Voice mode used to mean: speak, wait for the whole reply to generate, then listen to one long audio file. Now Hermes speaks clause-by-clause as the response streams, you can interrupt it mid-sentence by just talking (it stops, listens, and the model is told you cut in), and busy-aware silence detection means it doesn't talk over you. This works in CLI voice mode, on the desktop, and through gateway adapters. Talking to Hermes finally feels like a conversation, not a voicemail exchange. ( #69511 , #73862 , #74223 , #74000 , #69602 — @teknium1 , @OutThisLife ) 
 
 
 Wake words and hands-free control — Say your own open-vocabulary wake phrase ("hey Hermes", or anything you pick) and Hermes starts listening — detection runs on-device, so no audio leaves your machine while it waits. Multi-profile voice routing means different wake words can reach different profiles, and saying "stop" ends the voice chat on every surface without touching the keyboard. Your terminal is now something you can talk to from across the room. ( #70509 , #73106 , #73933 — @teknium1 ) 
 
 
 Voice on every platform — Send a voice note to Hermes on WhatsApp, Feishu, DingTalk, LINE, QQ, Photon, or Weixin and it's transcribed and answered; auto-TTS replies are delivered platform-aware (opus where platforms want opus, captions attached correctly). STT is now fully configurable — its own hermes tools category, GUI toggles, dashboard dropdowns, unified language resolution so transcripts stop coming back in the wrong language, and OpenAI's gpt-transcribe support. One unified spoken-text preprocessor cleans markdown, code, and URLs out of speech across all TTS providers. ( #73515 , #73508 , #73910 , #73513 , #73067 — @teknium1 ) 
 
 
 Research you can trust — grounded citations with fact-checking — The new grounded-citations skill makes Hermes produce research where every claim is backed by a verifiable source: quotes are matched against the actual page text (not hallucinated), citations link to the exact evidence, and a fact-checking mode turns the same machinery on any document or claim you hand it — it tells you what checks out, what doesn't, and what couldn't be verified. If you use Hermes for research, this is the difference between "sounds right" and "provably sourced." ( #71698 , #77104 — @teknium1 ) 
 
 
 Outbound webhooks — Hermes pushes events to your systems — Until now, integrating with Hermes meant polling or listening on a platform. Now Hermes pushes signed lifecycle events (session activity, turn completions, tool events) to any HTTP endpoint you register — with HMAC signatures so your receiver can verify authenticity. Wire Hermes into your CI, your home automation, your dashboards, or any service that speaks HTTP, with no polling loop. ( #69406 — @teknium1 ) 
 
 
 The desktop app becomes a platform — artifacts, plugin SDK, quick entry — Hermes desktop now renders artifacts : versioned cards with sandboxed live preview in a right-rail viewer, so generated HTML/apps run safely next to the chat. A real plugin SDK landed with Kanban as its founding plugin, ctx.download for handing users files, floating pane placement, and multiple GUI windows. A global-hotkey quick-entry window captures a thought into any session from anywhere in your OS. The desktop stopped being a chat client and started being a workbench. ( #72345 , #61173 , #74413 , #72315 , #68259 , #73143 — @OutThisLife , @teknium1 ) 
 
 
 Hermes speaks Agent-to-Agent — A2A v1.0 — A new bundled plugin implements the Agent-to-Agent protocol, so Hermes can discover, talk to, and be driven by other A2A-compatible agents. This closes issue #514 — one of the oldest open feature requests in the repo. If you're building multi-agent systems with heterogeneous stacks, Hermes now has a standard wire protocol for joining them. ( #77109 — @teknium1 ) 
 
 
 CLI power-user wave — !command runs a shell command instantly without spending a model turn. /init scans your project and generates (or updates) an AGENTS.md . /diff shows staged/all/session changes from any surface, /context breaks down exactly what's filling your context window, /focus gives you a reduced-output view with hidden-line recovery, and Ctrl+S stashes a half-written prompt into a browsable panel. Plus hermes import-agent migrates your Claude Code or Codex CLI setup into Hermes in one command. ( #72257 , #72178 , #72240 , #72242 , #72302 , #72262 , #72190 — @teknium1 , several salvaging long-standing community PRs) 
 
 
 Correct the agent mid-turn — redirects — If Hermes is heading the wrong way, you no longer have to /stop and re-explain. Type a correction while it works and the active turn is redirected: work in flight is preserved, the original prompt is kept, and the agent course-corrects with your new guidance. Paired with double-ESC draft discard and a composer undo stack, steering feels like editing, not restarting. ( #63104 , #72339 , #74736 — @OutThisLife ) 
 
 
 Tools that fix themselves — A sweep of self-recovery upgrades means the agent wastes far fewer turns on tool friction: truncated terminal output spills to a file the agent can read back, patch detects already-applied edits and diagnoses whitespace mismatches, write_file verifies content on disk, searches that match nothing probe for near-misses and recover, and common failure classes come back with actionable hints. The default tool-calling iteration limit also jumped 90 → 500 — long autonomous runs stopped hitting an artificial wall. ( #77041 , #76998 , #77024 , #77055 , #77011 , #76992 , #72176 — @teknium1 ) 
 
 
 Compression that respects your conversation — Context compression got a deep overhaul: proactive tool-result pruning for large-window models, per-turn micro-compaction that amortizes the cost instead of one giant pause, a guaranteed N-user-message tail so recent conversation always survives, progress-aware timeouts that stop punishing slow summary models, and ghost-skill defense so a pruned skill can never silently haunt a session. Thresholds are now configurable per-model and in absolute tokens. Long sessions stay coherent and stop stalling. ( #70254 , #75345 , #70250 , #71508 , #70275 — @teknium1 , @kshitijk4poor , salvaging multiple community PRs) 
 
 
 Smart approvals grow up — hermes approvals suggest mines your approval history into allowlist proposals, operators can customize the smart-approval policy, a consecutive-denial circuit breaker stops a misbehaving loop cold, and desktop pairing approvals are profile-correct with a proper surface to answer them from. Plus a new approval gate for docker/podman daemon-redirect commands. Less clicking "approve", without giving an inch of control. ( #72259 , #72186 , #72203 , #74446 , #71092 — @teknium1 , @OutThisLife ) 
 
 
 Faster everywhere, again — Prompt caching now covers tool schemas on native Anthropic without history loss. hermes -w cold start dropped ~14s → ~1.8s, hermes update no-ops got 2–6s faster, heavy SDKs lazy-load off the import path, config reads stopped deep-copying (54× faster on the telemetry gate), and the desktop shipped a second 60fps wave — streaming cost independent of transcript length, drag at 60fps with five streaming tabs, idle CPU near zero in the background. ( #76032 , #71637 , #74218 , #74204 , #71835 , #72346 , #75218 — @kshitijk4poor , @teknium1 , @OutThisLife ) 
 
 
 New places to run and be reached — Buzz lands as a bundled gateway platform (Block's Nostr-based messenger, with native WebSocket transport and NIP-42 auth), the Vercel AI Gateway provider and Vercel Sandbox terminal backend return modernized, desktop gains an SSH remote-backend connection mode, and the Relay shipped four phases of parity — media, interactive prompts, thread lifecycle, typing indicators — plus HSP personal + org skill sync. ( #73610 , #73761 , #74518 , #68130 , #71300 – #71624 , #66730 — @teknium1 , @yoniebans , @benbarclay ) 
 
 
 
 🎙️ Voice &amp; Speech 
 Conversational voice 
 
 Streaming, conversational TTS with barge-in across all surfaces; clause-by-clause synthesis for CLI voice mode + gateway adapters ( #69511 , #73862 — @OutThisLife , @teknium1 ) 
 Voice chat UX polish — busy-aware silence, stop hint, thinking sounds, barge-in fix; full-duplex turn listener (interrupt by voice during generation AND playback) ( #74000 , #74223 — @teknium1 ) 
 On-device wake words with open-vocabulary phrases + multi-profile voice routing; say "stop" to end voice chat hands-free on every surface ( #70509 , #73106 , #73933 — @teknium1 ) 
 The model is told when the user interrupts its spoken reply; desktop speaks the whole turn and idle-flushes held narration ( #69602 , #69936 — @OutThisLife , @teknium1 ) 
 15-item CLI/TUI voice-mode UX and environment fix wave ( #73520 — @teknium1 ) 
 
 TTS / STT infrastructure 
 
 Unified spoken-text preprocessing + speed/instructions/provider tool params; unified STT language resolution (fixes the wrong-language transcription class); global stt.language defaults to en ( #73513 , #73067 , #73100 — @teknium1 ) 
 Fully configurable STT — hermes tools category, GUI toggle/matrix, dashboard dropdowns, setup status; OpenAI gpt-transcribe support ( #73910 , #73853 — @teknium1 ) 
 Platform-aware auto-TTS voice delivery (opus platforms, streamed/global gap, captions); inbound voice classification/routing for Feishu, DingTalk, LINE, QQ, Photon, WhatsApp, Weixin ( #73508 , #73515 — @teknium1 ) 
 Command TTS/STT provider hardening — idle timeouts, env scrubbing, no-shell, path guards ( #73514 — @teknium1 ) 
 Sync per-sentence TTS synthesis pipelined with playback — the next sentence renders while the current one speaks ( #77355 — @kshitijk4poor ) 
 Discord voice PCM streams to ffmpeg stdin instead of a temp file ( #76970 — @kshitijk4poor ) 
 
 🏗️ Core Agent &amp; Architecture 
 Compression &amp; context 
 
 Proactive tool-result pruning for large-window models; per-turn micro-compaction; N-user tail guarantee ( compression.min_tail_user_messages ); bounded summarizer input with head+tail retention ( #70254 , #75345 , #70250 , #70249 — @teknium1 , @kshitijk4poor ) 
 Ghost-skill defense — [SKILL_PRUNED] markers, protected prune, deterministic survival; progress-aware timeouts; lock-contended compression soft-defers instead of exhausting ( #70275 , #71508 , #70285 — @teknium1 ) 
 Per-model threshold overrides; absolute token threshold ( compression.threshold_tokens ); opt-in idle-triggered compaction; opt-in progress notices; structured local logging for compression attempts ( #69339 , #69335 , #69360 , #70457 , #69338 — @teknium1 ) 
 Context-engine ABC grows select_context() + on_turn_complete() verbs (salvage of @chaos-xxl 's RFC work); engines ca

[... truncated for safety ...]

</details>