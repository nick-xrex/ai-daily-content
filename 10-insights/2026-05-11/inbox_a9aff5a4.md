---
id: inbox_a9aff5a4
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/1800-ruflo-releases-v3-7-0-alpha-22-discoverable-verifiable-8d87]]"
title: "v3.7.0-alpha.22 — Discoverable, Verifiable, Networked"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.22
source: ruflo-releases
published_at: 2026-05-11T04:31:59+00:00
fetched_at: 2026-05-22T18:13:42.127467+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.7.0-alpha.22 發布三大改進。首先，285 個 MCP tools 全數增加「何時使用」指南（「Use when native [X] is wrong because [concrete value-add]」格式），解決 Claude 傾向調用 native Task tool 的問題，並通過 CI guard 強制新 tool 必須附帶。其次，opt-in WireGuard mesh layer 用於 federation peers，信任層的 SUSPEND/EVICT 動作同步到 L3 AllowedIPs，已實作 nftables/pf firewall projection、witness attestation chain 與 3 個 operator MCP tools（federation_wg_status、_attest、_keyrotate）。第三，所有 102 項文檔化修復均密碼驗證（Ed25519），完整度 100%。該版本回應 AlphaSignal AI 審計的 6 項 gap，已修復 5 項：agent_spawn 現調用 Anthropic API 直接、workflow_execute 有真實 step executor + variable interpolation、WASM agent 檢測 stub 後路由至 Anthropic、auto-memory bloat 從 5,706 entries 降至 8 backend entries、tool discoverability 從 237/300 升至 0/285、fake simulate_benchmarks.py 已移除。"
key_points:
  - "285/285 MCP tools 增加「Use when X is wrong because Y」指南，由 CI guard 強制執行；User-visible effect：Claude 優先調用 Ruflo tools（cost tracking per agent、cross-session learning、swarm coordination）而非 native Task"
  - "WireGuard mesh opt-in，7 phases 中 1-6 已發布：manifest extension、key generation、WgMeshService、breaker integration、nftables/pf firewall projection、witness attestation chain；phase 7（wg-quick up）保持人工操作"
  - "審計修復：agent_spawn 改用 Anthropic API direct call、workflow_execute 支援 real step executor + pause/resume、WASM agent 檢測 stub 並路由至 LLM、auto-memory bloat 8 entries vs 5,706、tool discoverability 0/285 gap、benchmark integrity 移除 simulate_benchmarks.py"
tags: [mcp-tools, federation, tool-discovery, wireguard, audit-response]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.7.0-alpha.22 — Discoverable, Verifiable, Networked

Ruflo v3.7.0-alpha.22 發布三大改進。首先，285 個 MCP tools 全數增加「何時使用」指南（「Use when native [X] is wrong because [concrete value-add]」格式），解決 Claude 傾向調用 native Task tool 的問題，並通過 CI guard 強制新 tool 必須附帶。其次，opt-in WireGuard mesh layer 用於 federation peers，信任層的 SUSPEND/EVICT 動作同步到 L3 AllowedIPs，已實作 nftables/pf firewall projection、witness attestation chain 與 3 個 operator MCP tools（federation_wg_status、_attest、_keyrotate）。第三，所有 102 項文檔化修復均密碼驗證（Ed25519），完整度 100%。該版本回應 AlphaSignal AI 審計的 6 項 gap，已修復 5 項：agent_spawn 現調用 Anthropic API 直接、workflow_execute 有真實 step executor + variable interpolation、WASM agent 檢測 stub 後路由至 Anthropic、auto-memory bloat 從 5,706 entries 降至 8 backend entries、tool discoverability 從 237/300 升至 0/285、fake simulate_benchmarks.py 已移除。

### 重點
- 285/285 MCP tools 增加「Use when X is wrong because Y」指南，由 CI guard 強制執行；User-visible effect：Claude 優先調用 Ruflo tools（cost tracking per agent、cross-session learning、swarm coordination）而非 native Task
- WireGuard mesh opt-in，7 phases 中 1-6 已發布：manifest extension、key generation、WgMeshService、breaker integration、nftables/pf firewall projection、witness attestation chain；phase 7（wg-quick up）保持人工操作
- 審計修復：agent_spawn 改用 Anthropic API direct call、workflow_execute 支援 real step executor + pause/resume、WASM agent 檢測 stub 並路由至 LLM、auto-memory bloat 8 entries vs 5,706、tool discoverability 0/285 gap、benchmark integrity 移除 simulate_benchmarks.py

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.22)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ruflo v3.7.0-alpha.22 — "Discoverable, Verifiable, Networked" 
 
 Three big wins in this release: every MCP tool now tells Claude when to use it , the WireGuard mesh layer ships for federation peers who want trust changes to follow at the packet layer, and all 102 documented fixes are cryptographically verified end-to-end. Plus a handful of audit responses + bug fixes. 
 
 Install 
 npx ruflo@latest # 3.7.0-alpha.22 
npx claude-flow@latest # 3.7.0-alpha.22 
npx @claude-flow/cli@latest # 3.7.0-alpha.22 
npx @claude-flow/plugin-agent-federation@latest # 1.0.0-alpha.15 
 The headline change: every Ruflo tool now answers "when should Claude actually use this?" 
 Before this release, 279 of 285 MCP tools shipped descriptions that just said what they do (e.g. "Spawn an agent" , "Store data in memory" ). When Claude sees that next to native Task or Write , it has no signal to pick Ruflo over native — and it usually doesn't. 
 After: 285 of 285 tools have an explicit "Use when native [X] is wrong because [concrete value-add]; for [inverse case], native is fine" clause. Example: 
 
 agent_spawn : Spawn a Ruflo-tracked agent with cost attribution + memory persistence + swarm coordination. Use when native Task tool is wrong because you need cost tracking per agent / cross-session learning via patterns / coordination with other agents in a swarm topology. For one-shot subtasks with no learning loop, native Task is fine. 
 
 Same pattern across all 32 tool categories. ADR-112 documents the rule + the CI guard that keeps it enforced (any new tool shipping without guidance fails the build). 
 User-visible effect : Claude will actually call Ruflo tools where they add value — cost-tracked agents, persistent memory, swarm coordination — instead of falling through to native every time. 
 ADR-111 — WireGuard mesh for federation peers (opt-in) 
 @claude-flow/plugin-agent-federation@1.0.0-alpha.15 ships an opt-in WireGuard layer that hooks into the existing federation trust ladder + circuit breaker. When the breaker SUSPENDs or EVICTs a peer, the same transition propagates to WG AllowedIPs — a peer the trust layer just blocked can't reach the rest of the mesh at L3 either. 
 Phases shipped: manifest extension + key generation, WgMeshService, breaker integration, firewall projection ( nftables / pf ), witness attestation chain, and three operator MCP tools ( federation_wg_status , _attest , _keyrotate ). 
 Phase 7 (the actual wg-quick up ) stays operator-mediated — staged configs land in /tmp/adr-111-stage/ , operator reviews + activates manually. See docs/federation/phase7-mesh-bringup.md for the bringup procedure. 
 Audit response ( #1896 ) 
 External audit by AlphaSignal AI named six gaps in v3.6.30. Re-measured on current main with the v3.7.0-alpha work landed: 
 
 
 
 Gap 
 Article claim (v3.6.30) 
 Current main 
 Status 
 
 
 
 
 G1 — agent_spawn no LLM 
 In-memory Map, no subprocess 
 agent_execute calls Anthropic API directly 
 ✅ remediated 
 
 
 G3 — workflow_execute broken 
 Always returns "not found" 
 Real step executor + variable interpolation + pause/resume 
 ✅ remediated 
 
 
 G4 — WASM agent echoes 
 No LLM, returns "echo: X" 
 Detects stub + routes through Anthropic when ANTHROPIC_API_KEY set 
 ✅ remediated 
 
 
 G6 — auto-memory bloat 
 5,706 entries / 20 unique per message 
 Single routing call; 8 backend entries observed; no Trigram/Jaccard code 
 ✅ refuted 
 
 
 #1748 — tool discoverability 
 237/300 tools lack guidance 
 0/285 (this release fixes it) 
 ✅ resolved 
 
 
 Benchmark integrity 
 simulate_benchmarks.py + "84.8% SWE" 
 Both removed from main 
 ✅ cleaned 
 
 
 
 See #1896 for the full file-path-receipted writeup + ADR-095 status update. 
 Smaller fixes 
 
 #1892 — UI version banner no longer hardcoded. The statusline now reads @claude-flow/cli 's package.json at runtime so the UI matches ruflo doctor output. 
 Security — peer-content injection vector found during ADR-111 security audit and fixed ( readSafePeerWgFields validator). A compromised federation peer with a valid Ed25519 key could otherwise inject extra [Peer] blocks via newline-laden wgEndpoint . Closed before any user activated WG mesh. 
 
 Verification — 102/102 fixes cryptographically attested 
 Every documented fix in the witness manifest is now Ed25519-signed and verifiable end-to-end via node plugins/ruflo-core/scripts/witness/verify.mjs . New entries this release: ADR-111, ADR-112, #1892 . 
 What this release is NOT 
 
 A swarm-runtime rewrite. ADR-095 G2 (multi-process consensus) is still single-process for hive-mind; the federation plugin's transport is the only multi-host wire that's hardened. 
 A WASM-runtime rebuild. G4 is "echo + LLM fallback", not "full WASM sandbox with deterministic replay" — that's a separate ADR. 
 A benchmark publication. The fake simulate_benchmarks.py is gone but Ruflo still doesn't appear on the official SWE-bench leaderboard — by design until a real run is published. 
 
 Upgrade 
 If you're on any v3.7.0-alpha, npm i ruflo@latest is enough. If you're on v3.6.x: 
 # Snapshot first (sane practice): 
ruflo memory list &gt; backup-memory.txt
 # Then: 
npx ruflo@latest init --upgrade 
 Federation users wanting the opt-in WireGuard layer: npx @claude-flow/plugin-agent-federation@latest , then follow docs/federation/README.md . 
 Links 
 
 ADR-112 — tool discoverability 
 ADR-111 — federation WG mesh 
 Federation user guide 
 #1896 — audit response 
 #1748 — tool discoverability tracking

</details>