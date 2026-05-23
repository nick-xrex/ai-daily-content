---
id: inbox_aded27ae
source: hermes-agent-releases
source_type: rss
url: "https://github.com/NousResearch/hermes-agent/releases/tag/v2026.4.30"
author: "teknium1"
published_at: 2026-04-30T18:31:21+00:00
fetched_at: 2026-05-22T18:00:31.396884+00:00
content_hash: "c4d1afd462319f19fddc9b32a4c0afd9f13c7872ce5b3f415b50745a32970f03"
lang: en
caption_quality: None
raw: true
topics: []
---

# Hermes Agent v0.12.0 (2026.4.30)

Hermes Agent v0.12.0 (v2026.4.30) 
 Release Date: April 30, 2026 
 Since v0.11.0: 1,096 commits · 550 merged PRs · 1,270 files changed · 217,776 insertions · 213 community contributors (including co-authors) 
 
 The Curator release — Hermes Agent now maintains itself. An autonomous background Curator grades, prunes, and consolidates your skill library on its own schedule. The self-improvement loop that reviews what to save got a substantial upgrade. Four new inference providers, a 18th messaging platform, a 19th via Teams plugin, native Spotify + Google Meet integrations, ComfyUI and TouchDesigner-MCP moved from optional to bundled-by-default, and a ~57% cut to visible TUI cold start. 
 
 
 ✨ Highlights 
 
 
 Autonomous Curator — hermes curator runs as a background agent on the gateway's cron ticker (7-day cycle default). It grades your skill library, consolidates related skills, prunes dead ones, and writes per-run reports to logs/curator/run.json + REPORT.md . Archived skills are classified consolidated-vs-pruned via model + heuristic. Defense-in-depth gates protect bundled/hub skills from mutation. Unified under auxiliary.curator — pick the curator's model in hermes model , manage it from the dashboard. hermes curator status ranks skills by usage (most-used / least-used). ( #17277 , #17307 , #17941 , #17868 , #18033 ) 
 
 
 Self-improvement loop — substantially upgraded — The background review fork (the core of Hermes' self-improvement: after each turn it decides what memories/skills to save or update) is now class-first (rubric-based rather than free-form), active-update biased (prefers the skill the agent just loaded), handles references/ / templates/ sub-files, and properly inherits the parent's live runtime (provider, model, credentials actually propagate). Restricted to memory + skills toolsets so it can't sprawl. Memory providers shut down cleanly. Prior-turn tool messages excluded from the summary so the fork sees a clean context. ( #16026 , #17213 , #16099 , #16569 , #16204 , #15057 ) 
 
 
 Skill integrations — major expansion — ComfyUI v5 with official CLI + REST + hardware-gated local install, moved from optional to built-in by default ( #17610 , #17631 , #17734 ). TouchDesigner-MCP bundled by default, expanded with GLSL, post-FX, audio, geometry, and 9 new reference docs ( #16753 , #16624 , #16768 — @kshitijk4poor + @SHL0MS ). Humanizer skill ports a text-cleaner that strips AI-isms ( #16787 ). claude-design HTML artifact skill + design-md (Google DESIGN.md spec) + airtable salvage + skill_manage edits in external_dirs + direct-URL skill install + /reload-skills slash command. ( #16358 , #14876 , #16291 , #17512 , #16323 , #17744 ) 
 
 
 LM Studio — first-class provider — upgraded from a custom-endpoint alias to a full-blown native provider: dedicated auth, hermes doctor checks, reasoning transport, live /models listing. (Salvage of @kshitijk4poor 's #17061 .) ( #17102 ) 
 
 
 Four more new inference providers — GMI Cloud (first-class, salvage of #11955 — @isaachuangGMICLOUD ), Azure AI Foundry with auto-detection, MiniMax OAuth with PKCE browser flow (salvage #15203 ), Tencent Tokenhub (salvage of #16860 ). ( #16663 , #15845 , #17524 , #16960 ) 
 
 
 Pluggable gateway platforms + Microsoft Teams — the gateway is now a plugin host. Drop-in messaging adapters live outside the core, and Microsoft Teams is the first plugin-shipped platform. (Salvage of #17664 .) ( #17751 , #17828 ) 
 
 
 Tencent 元宝 (Yuanbao) — 18th messaging platform — native gateway adapter with text + media delivery. ( #16298 , #17424 ) 
 
 
 Spotify — native tools + bundled skill + wizard — 7 tools (play, search, queue, playlists, devices) behind PKCE OAuth, interactive setup wizard, bundled skill, surfacing in hermes tools , cron usage documented. ( #15121 , #15130 , #15154 , #15180 ) 
 
 
 Google Meet plugin — join calls, transcribe, speak, follow up. Realtime OpenAI transport + Node bot server, full pipeline bundled as a plugin. ( #16364 ) 
 
 
 hermes -z one-shot mode + hermes update --check — non-interactive hermes -z &lt;prompt&gt; with --model / --provider / HERMES_INFERENCE_MODEL . hermes update --check preflight. Opt-in pre-update HERMES_HOME backup. ( #15702 , #15704 , #15841 , #16539 , #16566 ) 
 
 
 Models dashboard tab + in-browser model config — rich per-model analytics, switch main + auxiliary models from the dashboard. ( #17745 , #17802 ) 
 
 
 Remote model catalog manifest — OpenRouter + Nous Portal model catalogs are now pulled from a remote manifest so new models show up without a release. ( #16033 ) 
 
 
 Native multimodal image routing — images now route based on the model's actual vision capability rather than provider defaults. ( #16506 ) 
 
 
 Gateway media parity — native multi-image sending across Telegram, Discord, Slack, Mattermost, Email, and Signal; centralized audio routing with FLAC support + Telegram document fallback. ( #17909 , #17833 ) 
 
 
 TUI catches up to (and past) the classic CLI — LaTeX rendering ( @austinpickett ), /reload .env hot-reload, pluggable busy-indicator styles ( @OutThisLife , #13610 ), opt-in auto-resume of last session, expanded light-terminal auto-detection, session delete from /resume picker with d , modified mouse-wheel line scroll, and a /mouse toggle that kills ConPTY's phantom mouse injection ( @kevin-ho ). ( #17175 , #17286 , #17150 , #17130 , #17113 , #17668 , #17669 , #15488 ) 
 
 
 Observability + achievements plugins — bundled Langfuse observability plugin (salvage #16845 ) + bundled hermes-achievements plugin that scans full session history. ( #16917 , #17754 ) 
 
 
 TTS provider registry + Piper local TTS — pluggable tts.providers.&lt;name&gt; registry; Piper ships as a native local TTS provider. (Closes #8508 .) ( #17843 , #17885 ) 
 
 
 Vercel Sandbox backend — Vercel sandboxes as an execute_code/terminal backend ( @kshitijk4poor ). ( #17445 ) 
 
 
 Secret redaction off by default — default flipped to off. Prevents the long-standing patch-corruption incidents where fake secret-shaped substrings mangled tool outputs. Opt in via redaction.enabled: true when you need it. ( #16794 ) 
 
 
 Cold-start performance — visible TUI cold start cut ~57% via lazy agent init ( @OutThisLife ), lazy imports of OpenAI / Anthropic / Firecrawl / account_usage, mtime-cached load_config() , memoized get_tool_definitions() with TTL-cached check_fn results, precompiled dangerous-command patterns. ( #17190 , #17046 , #17041 , #17098 , #17206 ) 
 
 
 Configurable prompt cache TTL — prompt_caching.cache_ttl (5m default, 1h opt-in — cost savings for bursty sessions that keep cache warm). Salvage of #12659 . ( #15065 ) 
 
 
 
 🧠 Autonomous Curator &amp; Self-Improvement Loop 
 Curator — autonomous skill maintenance 
 
 hermes curator as a background agent — runs on the gateway's cron ticker, 7-day cycle by default, umbrella-first prompt, inherits parent config, unbounded iterations ( #17277 — issue #7816 ) 
 Per-run reports — logs/curator/run.json + REPORT.md per cycle ( #17307 ) 
 Consolidated vs pruned classification — archived skills split with model + heuristic ( #17941 ) 
 hermes curator status — ranks skills by usage, shows most-used and least-used ( #18033 ) 
 Unified under auxiliary.curator — pick the model in hermes model , configure from the dashboard ( #17868 ) 
 Documentation — dedicated curator feature page on the docs site ( #17563 ) 
 Fix: seed defaults on update, create logs/curator/ directory, defer fire import ( #17927 ) 
 Fix: scan nested archive subdirs in restore_skill ( @0xDevNinja ) ( #17951 ) 
 Fix: use actual skill activity in curator status ( @y0shua1ee ) ( #17953 ) 
 Fix: skill_manage refuses writes on pinned skills; pinning now blocks curator writes ( #17562 , #17578 ) 
 Fix: bump_use() wired into skill invocation + preload + skill_view (salvage #17782 ) ( #17932 ) 
 
 Self-improvement loop (background review fork) 
 
 Class-first skill-review prompt — rubric-based grading rather than free-form "should this update" ( #16026 ) 
 Active-update bias — prefers updating skills the agent just loaded, handles references/ + templates/ sub-files ( #17213 ) 
 Fork inherits parent's live runtime — provider, model, credentials actually propagate now ( #16099 ) 
 Scoped toolsets — review fork restricted to memory + skills (no shell, no web) ( #16569 ) 
 Clean shutdown — background review memory providers exit properly (salvage #15289 ) ( #16204 ) 
 Clean context — prior-history tool messages excluded from review summary (salvage #14967 ) ( #15057 ) 
 
 
 🧩 Skills Ecosystem 
 Skill integrations — newly bundled or promoted 
 
 ComfyUI v5 — official CLI + REST + hardware-gated local install; moved from optional to built-in ( #17610 , #17631 , #17734 , #17612 ) 
 TouchDesigner-MCP — bundled by default ( #16753 — @kshitijk4poor ), expanded with GLSL, post-FX, audio, geometry references ( #16624 ), 9 new reference docs ( #16768 — @SHL0MS ) 
 Humanizer — strips AI-isms from text ( #16787 ) 
 claude-design — HTML artifact skill with disambiguation from other design skills ( #16358 ) 
 design-md — Google's DESIGN.md spec skill ( #14876 ) 
 airtable — salvaged skill + skill API keys wired into .env ( #15838 ) ( #16291 ) 
 pretext — creative browser demos with @chenglou/pretext ( #17259 ) 
 spike + sketch — throwaway experiments + HTML mockups, adapted from gsd-build ( #17421 ) 
 
 Skills UX 
 
 Install skills from a direct HTTP(S) URL — hermes skills install &lt;url&gt; ( #16323 ) 
 /reload-skills slash command (salvage #17670 ) ( #17744 ) 
 hermes skills list shows enabled/disabled status ( #16129 ) 
 skill_manage refuses writes on pinned skills ( #17562 ) 
 skill_manage edits external_dirs skills in place (salvage #9966 ) ( #17512 , #17289 ) 
 Fix: inline-shell rendering in skill_view ( #15376 ) 
 Fix: exclude .archive/ from skill index walk (salvage #17639 ) ( #17931 ) 
 Fix: dedicated docs page per bundled + optional skill ( #14929 ) 
 Fix: google-workspace shared HERMES_HOME helper + ship deps as optional extra ( #15405 ) 
 Fix: auto-wrap ASCII-art code blocks in generated skill pages ( #16497 ) 
 Point agent at hermes-agent skill + docs site for Hermes questions ( #16535 ) 
 
 
 🏗️ Core Agent &amp; Architecture 
 Provider &amp; Model Support 
 New providers 
 
 GMI Cloud — first-class API-key provider on par with Arcee/Kilocode/Xiaomi (salvage of #11955 — @isaachuangGMICLOUD ) ( #16663 ) 
 Azure AI Foundry — auto-detection, full wiring ( #15845 ) 
 LM Studio — upgraded from custom-endpoint alias to first-class provider: dedicated auth, doctor checks, reasoning transport, live /models (salvage of #17061 — @kshitijk4poor ) ( #17102 ) 
 MiniMax OAuth — PKCE browser flow with full OAuth integration (salvage #15203 ) ( #17524 ) 
 Tencent Tokenhub — new provider (salvage of #16860 ) ( #16960 ) 
 
 Model catalog 
 
 Remote model catalog manifest — OpenRouter + Nous Portal catalogs pulled from remote manifest so new models show up without a release ( #16033 ) 
 openai/gpt-5.5 and gpt-5.5-pro added to OpenRouter + Nous Portal ( #15343 ) 
 deepseek-v4-pro and deepseek-v4-flash added ( #14934 ) 
 qwen3.6-plus added to Alibaba-supported models ( #16896 ) 
 Gemini free-tier keys blocked at setup with 429 guidance surfacing ( #15100 ) 
 
 Model configuration 
 
 Configurable prompt_caching.cache_ttl — 5m default, 1h opt-in (salvage #12659 ) ( #15065 ) 
 /fast whitelist broadened to all OpenAI + Anthropic models ( #16883 ) 
 auxiliary.extra_body.reasoning translates into Codex Responses API ( #17004 ) 
 hermes fallback command for managing fallback providers ( #16052 ) 
 
 Agent Loop &amp; Conversation 
 
 Native multimodal image routing — based on model vision capability, not provider defaults ( #16506 ) 
 Delegate child_timeout_seconds default bumped to 600s ( #14809 ) 
 Diagnostic dump when subagent times out with 0 API calls ( #15105 ) 
 Gateway busts cached agent on compression/context_length config edits ( #17008 ) 
 Opt-in runtime-metadata foot

[... truncated for safety ...]