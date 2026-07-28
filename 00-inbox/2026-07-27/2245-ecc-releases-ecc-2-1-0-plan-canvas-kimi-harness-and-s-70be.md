---
id: inbox_f434fbb3
source: ecc-releases
source_type: rss
url: "https://github.com/affaan-m/ECC/releases/tag/v2.1.0"
author: "github-actions[bot]"
published_at: 2026-07-27T19:11:49+00:00
fetched_at: 2026-07-27T22:45:53.240187+00:00
content_hash: "70be48039e4d357e59675df5690309adad22f3eaef8236a5671349758c5137c9"
lang: en
caption_quality: None
raw: true
topics: []
---

# ECC 2.1.0: Plan Canvas, Kimi Harness, and Self-Hosted Compute

ECC 2.1.0: Plan Canvas, Kimi Harness, and Self-Hosted Compute 
 ECC 2.1 turns plan review into a visual loop and opens the harness to self-hosted models. Plan Canvas lets you review agent plans in the browser. Point at the part you mean instead of retyping it in chat. A new Kimi Code install target and a verified Itô GPU path make ECC + open-source models a first-class setup, backed by our public sponsors: Moonshot AI (Kimi), Itô, and Atlas Cloud. 
 Plan Canvas: review plans by pointing, not retyping 
 
 Download the MP4 demo 
 /plan ends with a confirm gate, and until now that review was a wall of markdown in the terminal. Now the agent opens the plan in a loopback-only browser canvas: 
 
 Click elements or select text to attach numbered annotations 
 Chat with the agent from a side rail while it works in the terminal 
 Approve plan / Request changes buttons map directly onto /plan 's CONFIRM gate 
 Mermaid diagrams, tables, and task lists render natively; file edits live-reload the page 
 Model- and harness-agnostic: a plain CLI + JSON protocol ( ecc-plan-canvas ), no Claude-only dependency 
 
 Kimi harness: Moonshot AI partnership 
 ECC now installs directly into Kimi Code ( --target kimi ). Kimi Code discovers the installed .kimi/AGENTS.md instructions and .kimi/skills/ workflows natively: 
 bash ./install.sh --target kimi --profile minimal
npx ecc doctor --target kimi
kimi 
 Self-host on Itô GPUs 
 Run ECC against any self-hosted open-source model. If you need GPU capacity, Itô is ECC's preferred compute sponsor. The integration shipped guarded end to end: 
 
 ecc ito find : opt-in bridge to the canonical Itô CLI that submits a live, authenticated RFQ (it does not reserve capacity) 
 Guarded live node qualification and read-only compute handoff 
 Credential-bearing CLI shims are rejected outright 
 
 The sponsorship link itself is passive: it does not invoke an RFQ, reserve capacity, provision compute, or configure serving. Managed inference through Itô is not live yet. Any GPU provider works, and ECC stays provider-agnostic. 
 Partners 
 Moonshot AI (Kimi) , Itô , and Atlas Cloud are now public sponsors of ECC. The README documents a recommended self-host path: Itô for GPU capacity, a Kimi checkpoint served behind a compatible endpoint, then Kimi Code + ECC on top. Each choice remains separate and swappable. 
 Also in 2.1 
 
 Hermes and OpenClaw install targets : two more harnesses join Claude Code, Codex, OpenCode, Cursor, Gemini, Zed, Copilot, and Kimi 
 Codex ECC navigation guide : find the right skill/command surface from inside Codex 
 GateGuard path exemptions ( GATEGUARD_EXEMPT_GLOBS ) and configurable instinct injection (count + confidence threshold) 
 PostToolUse hooks consolidated into sync/async dispatchers, with fewer processes per tool call 
 Supply-chain hardening : the installer runtime passes strict vetting, and the pre-commit secret scan now catches Anthropic API keys ( sk-ant-... ) 
 A long tail of community fixes across OpenCode, Windows, bun lockfiles, the dashboard, and project detection 
 
 The catalog now stands at 67 agents, 281 skills, and 94 command shims (2.0.0 shipped 64/261/84), plus hooks, rules, memory, continuous learning, and AgentShield. 
 Install or upgrade 
 /plugin marketplace add https://github.com/affaan-m/ECC
/plugin install ecc@ecc
 
 Existing installs: /plugin update ecc 
 Community 
 Join the ECC community for release announcements, questions, and Show and Tell: 
 https://discord.gg/36yGMHGFbR 
 Full changelog: v2.0.0...v2.1.0 
 New Contributors 
 
 @legeZZZ made their first contribution in #2200 
 @tongshu2023 made their first contribution in #2216 
 @mohameddsh3ban made their first contribution in #2195 
 @fiedler-itlabs made their first contribution in #2240 
 @daiki75 made their first contribution in #2245 
 @wellkilo made their first contribution in #2194 
 @rameshvr made their first contribution in #2144 
 @aaronjmars made their first contribution in #2185 
 @orbisai0security made their first contribution in #2149 
 @xwang4-svg made their first contribution in #2186 
 @kriptoburak made their first contribution in #2199 
 @lamenting-hawthorn made their first contribution in #2235 
 @mdayan8 made their first contribution in #2100 
 @Naominour made their first contribution in #2188 
 @Malphite10 made their first contribution in #2197 
 @cogiwimute367-create made their first contribution in #2251 
 @z3tz3r0 made their first contribution in #2250 
 @rockwellwindsor made their first contribution in #2258 
 @stroland02 made their first contribution in #2202 
 @hretheum made their first contribution in #2221 
 @BERORINPO made their first contribution in #2234 
 @Victor-Casado made their first contribution in #2236 
 @itkdm made their first contribution in #2241 
 @leoeletronics made their first contribution in #2267 
 @Seekers2001 made their first contribution in #2118 
 @lucaszhu-hue made their first contribution in #2279 
 @kapil971390 made their first contribution in #2292 
 @danielnguyenfinhub made their first contribution in #2342 
 @gpitrella made their first contribution in #2355 
 @Angad2005 made their first contribution in #2366 
 @quadcent made their first contribution in #2133 
 @SiaoZeng made their first contribution in #2383 
 @Tahiti18 made their first contribution in #2307 
 @phobicdotno made their first contribution in #2343 
 @sshworld made their first contribution in #2358 
 @cd1amond made their first contribution in #2346 
 @Tanaka-VivereGratis made their first contribution in #2388 
 @KyawZinLatt made their first contribution in #2319 
 @dieudonneAwa made their first contribution in #2288 
 @carloscarvallo made their first contribution in #2273 
 @mc856 made their first contribution in #2274 
 @jvirgovic made their first contribution in #2338 
 @m18897829375 made their first contribution in #2336 
 @jack-finance-able made their first contribution in #2390 
 @yerros made their first contribution in #2275 
 @YuhaoLin2005 made their first contribution in #2377 
 @Cb2i made their first contribution in #2437 
 @28winz-bot made their first contribution in #2422 
 @sutazca made their first contribution in #2425 
 @nidelson made their first contribution in #2420 
 @juujb made their first contribution in #2416 
 @Zalasyu made their first contribution in #2432 
 @Lxcardoza993 made their first contribution in #2433 
 @haelyra made their first contribution in #2467 
 @thejesh23 made their first contribution in #2515 
 @nankingjing made their first contribution in #2501 
 @samartomar made their first contribution in #2503 
 @fletcherm-hub made their first contribution in #2460 
 @someiyoshino-lab made their first contribution in #2471 
 @WinterSold1er made their first contribution in #2511 
 @EmadDoughan made their first contribution in #2543 
 @Oleksandr-Kh4 made their first contribution in #2529 
 @latreon made their first contribution in #2536 
 
 Full Changelog : v2.0.0...v2.1.0