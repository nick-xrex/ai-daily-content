---
id: inbox_d770a39a
date: 2026-07-20
source_ref: "[[00-inbox/.../inbox_d770a39a]]"
title: "Hermes Agent v0.19.0 (2026.7.20) — The Quicksilver Release"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.7.20
source: hermes-agent-releases
published_at: 2026-07-20T18:44:28+00:00
fetched_at: 2026-07-21T01:07:55.277191+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent v0.19.0（v2026.7.20）發布「Quicksilver Release」，涵蓋性能、安全及協作功能的重大改進。冷啟動延遲從 4.3 秒大幅下降至 0.9 秒（～80% 改善），跨 CLI、Gateway、Desktop、TUI 生效；Desktop 應用的 Markdown 流式渲染速度提升 14 倍，新增虛擬化 diff 與 session 快速切換。推理模型預設流式顯示思考過程，無需等待 spinner。新增終端訂閱管理命令（/subscription、/topup），LLM 驅動的智能命令審批預設啟用（獨立評估每條命令，降低審批疲勞），Bitwarden 與 1Password 密碼管理器整合，子代理實時轉錄及持久交付分類帳（防止網關崩潰導致回應丟失）。新增 Fireworks AI、DeepInfra 與 Upstage Solar 供應商，支援 GPT-5.6、grok-4.5、claude-fable-5、claude-sonnet-5 等最新模型；推理努力等級新增 max/ultra 層級，可按模型、任務、MoA 預設獨立配置。Session 導出支援 Markdown、HTML、Hugging Face 追蹤格式與可選祕密掩蔽。安全加固涵蓋憑證隔離、媒體文件讀取防護、webhook 大小限制、Token 前綴檢測等。"
key_points:
  - "冷啟動 4.3s → 0.9s (80% 改善)；Desktop Markdown 流式渲染 14 倍加速，虛擬化 diff 與 session 切換提升原生應用感受"
  - "智能命令審批預設啟用：LLM 獨立評估每條 flagged command，個別判決細化避免審批疲勞；支援 Bitwarden/1Password 秘密來源整合（pluggable SecretSource 介面）"
  - "新供應商支援（Fireworks、DeepInfra、Upstage）；新模型（GPT-5.6、grok-4.5、claude-fable-5、sonnet-5）；推理努力 max/ultra 層級；子代理實時轉錄 + 持久交付分類帳防止回應丟失"
tags: [hermes-agent, performance-optimization, agent-orchestration, smart-approvals, secret-integration]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.19.0 (2026.7.20) — The Quicksilver Release

Hermes Agent v0.19.0（v2026.7.20）發布「Quicksilver Release」，涵蓋性能、安全及協作功能的重大改進。冷啟動延遲從 4.3 秒大幅下降至 0.9 秒（～80% 改善），跨 CLI、Gateway、Desktop、TUI 生效；Desktop 應用的 Markdown 流式渲染速度提升 14 倍，新增虛擬化 diff 與 session 快速切換。推理模型預設流式顯示思考過程，無需等待 spinner。新增終端訂閱管理命令（/subscription、/topup），LLM 驅動的智能命令審批預設啟用（獨立評估每條命令，降低審批疲勞），Bitwarden 與 1Password 密碼管理器整合，子代理實時轉錄及持久交付分類帳（防止網關崩潰導致回應丟失）。新增 Fireworks AI、DeepInfra 與 Upstage Solar 供應商，支援 GPT-5.6、grok-4.5、claude-fable-5、claude-sonnet-5 等最新模型；推理努力等級新增 max/ultra 層級，可按模型、任務、MoA 預設獨立配置。Session 導出支援 Markdown、HTML、Hugging Face 追蹤格式與可選祕密掩蔽。安全加固涵蓋憑證隔離、媒體文件讀取防護、webhook 大小限制、Token 前綴檢測等。

### 重點
- 冷啟動 4.3s → 0.9s (80% 改善)；Desktop Markdown 流式渲染 14 倍加速，虛擬化 diff 與 session 切換提升原生應用感受
- 智能命令審批預設啟用：LLM 獨立評估每條 flagged command，個別判決細化避免審批疲勞；支援 Bitwarden/1Password 秘密來源整合（pluggable SecretSource 介面）
- 新供應商支援（Fireworks、DeepInfra、Upstage）；新模型（GPT-5.6、grok-4.5、claude-fable-5、sonnet-5）；推理努力 max/ultra 層級；子代理實時轉錄 + 持久交付分類帳防止回應丟失

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v2026.7.20)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Hermes Agent v0.19.0 (2026.7.20) — The Quicksilver Release

Hermes Agent v0.19.0 (v2026.7.20) 
 Release Date: July 20, 2026 
 Since v0.18.0: ~2,245 commits · ~1,065 merged PRs · ~2,465 files changed · ~300,000 insertions · ~36,000 deletions · ~3,300 issues closed · 450+ community contributors 
 
 The Quicksilver Release. Hermes is the messenger god, and this window we made him move like it. First-turn time-to-first-token dropped ~80% on every platform , reasoning streams live by default, the desktop app got a ~20-PR speed overhaul (14× faster streaming markdown, virtualized diffs, snappy session switching), and the TUI renders markdown incrementally. Around that speed spine: you can now manage your Nous subscription without leaving the terminal , plug Bitwarden and 1Password straight into Hermes, let smart approvals judge flagged commands for you by default, watch your subagents work live , and trust that a finished response survives a gateway crash thanks to a durable delivery ledger. This release also rolls up everything from the v0.18.1 and v0.18.2 infrastructure patch tags — those windows are fully documented here. 
 
 
 ✨ Highlights 
 
 
 Hermes got dramatically faster — first token in a fraction of the time — Cold-start "Initializing agent..." used to eat ~4.3 seconds before your first turn even reached the model; it's now ~0.9s, an ~80% cut that applies to the CLI, gateway, TUI, desktop, and cron alike. Round 2 attacked what you see while waiting: reasoning models now stream their thinking live by default (no more staring at a spinner for 30 seconds), and the response box paints per token instead of per line. If Hermes ever felt like it took a deep breath before answering, that breath is gone. ( #59332 , #59389 — @teknium1 ) 
 
 
 The desktop app speed wave — 20+ targeted perf PRs — Long replies used to cost 14× more CPU in the markdown splitter than they do now; giant diffs froze the review pane until we virtualized it; switching sessions thrashes layout no more. Streaming no longer re-renders the sidebar and every tool row per token, profile backends pre-warm on hover intent, and boot-hidden panes mount at idle instead of on the cold-start critical path. The net effect: the desktop app feels like a native app under load, even with huge transcripts and busy agents. ( #67154 , #67818 , #65898 , #66033 , #66747 , #67742 and more — @OutThisLife ) 
 
 
 Manage your Nous plan from the terminal — /subscription and /topup — Changing your subscription used to mean a trip to the billing website. Now /subscription opens a full flow right in the TUI or classic CLI: see your plan and remaining allowance, preview exactly what an upgrade costs ("Pay $46.30 &amp; upgrade now") or when a downgrade takes effect, and apply it — with scheduled-change banners and undo. The desktop app got a matching billing settings tab. Your wallet never has to leave the keyboard. ( #51639 , #61054 , #61067 — @alt-glitch ) 
 
 
 Smart approvals are now the default — When Hermes wants to run a flagged command, an LLM reviewer now assesses it independently instead of asking you to approve every single one — and each verdict covers only that exact command, so a later command matching the same pattern gets its own review. Combined with the new user-defined deny rules (which block commands even under yolo mode) and /deny &lt;reason&gt; (which tells the agent why you refused so it course-corrects), day-to-day approval fatigue drops sharply without giving up control. ( #62661 , #59164 , #54518 — @teknium1 ) 
 
 
 Plug your password manager into Hermes — Bitwarden &amp; 1Password secret sources — API keys no longer have to live in a plaintext .env . A new pluggable SecretSource interface lets Hermes fetch secrets from Bitwarden and 1Password ( op:// references) at load time, with multiple vaults enabled simultaneously, deterministic precedence, conflict warnings, and per-variable provenance. This consolidated eleven competing community PRs into one orchestrated interface — future vault providers drop in as plugins. ( #59498 — @teknium1 , 1Password provider salvaged from @hwrdprkns ) 
 
 
 Watch your subagents work — live transcripts + durable background delegation — delegate_task dispatches now return live transcript files you can tail -f the moment the subagents launch: every tool call, result, and streamed reply, one human-readable log per child. And background delegation completions are now durable — if the process restarts mid-run, results are restored and delivered through an ownership-checked ledger instead of vanishing. Fan out a fleet, watch any worker live, and never lose the results. ( #67479 , #63494 — @teknium1 ) 
 
 
 A finished answer can no longer be lost — the delivery-obligation ledger — If the gateway died between generating your response and confirming the platform actually delivered it, that answer used to be silently gone (and you'd paid for the turn). Final responses are now recorded in a durable ledger in state.db around the platform send and redelivered on the next boot — closing a P1 silent-loss window for Telegram, Discord, Slack, and every other channel. ( #67181 — @teknium1 ) 
 
 
 One gateway, many profiles — profile-based message routing — A single multiplexed gateway sharing one bot token can now route specific guilds, channels, or threads to different profiles — each with fully isolated config, skills, memory, and secrets. Point your work Discord server at the work profile and your hobby server at personal , from one bot. A second multiplex hardening wave means one misconfigured profile can no longer take down the whole gateway. ( #64835 salvaging @Burgunthy , #65700 , #60589 — @teknium1 , @benbarclay + six salvaged contributors) 
 
 
 New providers and the newest frontier models — Fireworks AI and DeepInfra land as first-class providers (Fireworks with cost estimation and a #2 slot in the provider picker), Upstage Solar joins via salvage, and the model catalogs picked up GPT-5.6 (Sol/Terra/Luna + Pro variants, wired end-to-end across every route) , grok-4.5 (GA) , moonshotai/kimi-k3 , claude-fable-5 / claude-sonnet-5 , and GA tencent/hy3 — plus LM Studio JIT model loading for local setups. ( #62593 , #63969 , #61616 — @kshitijk4poor completing @rob-maron 's #61578 , #60887 , #65913 , #64541 , #65472 ) 
 
 
 Crank the thinking to max — new reasoning effort tiers and per-model control — Reasoning effort gained max and ultra levels (GPT-5.6 and Codex's top tiers), selectable everywhere from the CLI to the desktop, with sane clamping on providers with smaller scales. You can now also pin per-model reasoning-effort overrides in config, set per-slot effort in MoA presets (your advisors think hard, your synthesizer stays fast), and per-task effort for auxiliary models. Thinking depth is now a dial, not a global switch. ( #62650 , #64458 , #64631 , #64597 — @teknium1 ) 
 
 
 Your sessions, your data — export everything — hermes sessions export now writes Markdown, Quarto, HTML, prompt-only, and even Hugging Face-ready trace formats, with the full filter surface (age, workspace, platform), an opt-in --redact secret-scrubbing pass, and compacted-session lineage stitched into one logical export. Pair with the new prune filters and bulk archive to keep your session store tidy. Your conversation history is a real dataset now, not a black box. ( #60186 salvaging @web3blind , #60492 , #60507 , #59327 — @teknium1 ) 
 
 
 Security hardening round — This window closed a long list of credential-surface gaps: Vertex credentials scoped away from subprocess env and through profile secret scopes, media/vision/image-gen local-file reads routed through one shared credential-read guard, a webhook body-size-cap sweep across every aiohttp server, bot-token redaction in Telegram transport errors, Fireworks token prefixes added to the redactor, six P1 browser/MEDIA/.env hardening PRs salvaged in one pass, and CI hardened against untrusted-ref interpolation. ( #57660 , #58709 , #59215 , #56582 , #57842 — @teknium1 , @srojk34 , @kshitijk4poor , @jquesnelle ) 
 
 
 
 ⚡ Performance — the speed spine 
 First-turn latency (all platforms) 
 
 ~80% TTFT cut — Discord capability detection off the critical path (token-keyed 24h disk cache + background refresh), Ollama probe skipped for known non-Ollama providers, agent-init blocking work removed; cold submit→dispatch ~4.3s → ~0.9s ( #59332 — @teknium1 ) 
 Perceived-latency round 2 — display.show_reasoning default ON (watch the model think instead of a spinner), per-token response-box painting with width-aware force-flush, prompt-build caching, mtime-cached timezone resolution ( #59389 — @teknium1 ) 
 Segment mixed tool batches to recover lost concurrency; drop per-call base64 re-serialization from request-size estimates ( #64460 , #67788 — @teknium1 , @OutThisLife ) 
 
 Desktop speed wave 
 
 14× less splitter CPU via incremental block lexing for streaming markdown; virtualized review-pane diffs (no more full-Shiki freeze); snappy session switching on large transcripts; killed the layout-thrash cascade on session switch ( #67154 , #67818 , #65898 , #66033 — @OutThisLife ) 
 Cut startup serialization + per-turn REST amplification; pre-warm profile backends and gateway sockets on hover intent; idle-mount boot-hidden panes; fast model picker + dialogs ( #66747 , #66347 , #67857 , #66470 — @OutThisLife ) 
 Stop per-token sidebar + tool-row re-renders during streaming; stop eager JSON.stringify of every tool's args/result; scope tool-diff subscriptions; batch sidebar session slices into one profile-DB pass; targeted file-tree revalidation; rAF-coalesced sash resizes ( #67742 , #67842 , #67195 , #67245 , #67824 , #67838 , #67844 — @OutThisLife ) 
 Systematized perf benchmark harness with trustworthy cold-start + first-token measurement, replacing 12 one-off scripts ( #67466 , #67697 — @OutThisLife ) 
 
 Everywhere else 
 
 TUI renders streamed markdown incrementally per block ( #67236 — @OutThisLife ) 
 Skill discovery cached by scan signature; snapshot manifest builds ~5× faster; text prefilter before AST parse in tool discovery ( #61414 , #61131 , #63941 — @kshitijk4poor , @ethernet8023 ) 
 Copy-on-write message prep instead of full deepcopy; model-metadata probe-cache cluster; gateway session.resume model + display history from one SELECT ( #61133 , #61368 , #67247 — @kshitijk4poor , @OutThisLife ) 
 hermes update skips npm install when Node manifests are unchanged; dashboard session-list payloads trimmed + messages paginated ( #61580 , #60883 — @kshitijk4poor ) 
 Byte-stable gateway system prompts — pinned session-context render keeps the prompt cache alive across turns ( #67403 — @kshitijk4poor ) 
 
 🏗️ Core Agent &amp; Architecture 
 Providers &amp; models 
 
 Fireworks AI provider with cost estimation + cached picker price columns, promoted to #2 in provider pickers ( #62593 , #65476 , #65214 — @teknium1 ) 
 DeepInfra hardened integration; Upstage Solar provider ( #42231 salvage) ( #63969 , #64541 — @kshitijk4poor ) 
 GPT-5.6 (Sol/Terra/Luna + Pro) end-to-end — context lengths, native/Codex catalogs, pricing, compaction caps across every route ( #61616 — @kshitijk4poor , building on @rob-maron ) 
 grok-4.5 (GA) catalog + reasoning allowlist; kimi-k3 on Nous Portal + OpenRouter (kimi-k2.x retired) + K3 discovery on the Kimi Coding endpoint; claude-fable-5 / claude-sonnet-5 / fugu-ultra curated; GA tencent/hy3 ( #60887 , #65913 , #65922 , #56617 , #60943 — @teknium1 ) 
 Catalog-labeled silent default (GLM-5.2) + bare-provider /model cost-safe routing; LM Studio JIT load mode; adaptive thinking for Kimi-family Anthropic endpoints ( #64771 , #65472 , #67606 — @teknium1 , @kshitijk4poor ) 
 GLM-5.2 native reasoning_effort controls; Gemini request-context improvements; extra HTTP headers for LLM API calls; per-client model routing on the API server ( #58884 , #61873 — @vishal-dharm , #57038 , #57028 — @teknium1 ) 
 Claude Sonnet 5 fully wired — curated lists, intro

[... truncated for safety ...]

</details>