---
id: inbox_c9aaf92d
date: 2026-07-29
source_ref: "[[00-inbox/.../inbox_c9aaf92d]]"
title: "Ruflo v3.32.29: Capability Brain — Corrected Stable Train"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.29
source: ruflo-releases
published_at: 2026-07-29T04:41:05+00:00
fetched_at: 2026-07-31T01:32:51.966304+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.29 發布，這是 v3.32.28 的修正版（v3.32.28 因發布憑證拒絕未正式發布）。v3.32.29 推進 ruflo/claude-flow/@claude-flow/cli 到 3.32.29，聯邦插件升級到 1.0.0-alpha.18。核心創新是 Ruflo Capability Brain：將原本只知曉 61 個工具的 MCP guidance catalog 升級為可發現全部 353 個工具的實時註冊表，支持按域名過濾、健康檢查、授權驗證。v3.32.29 定義了 12 步實現循環（recall→inspect→route→plan→execute→test→validate→benchmark→optimize→receipt→handoff→authorized publish）和新的聯邦簽名機制（JCS/Ed25519）、Cognitum 產品 API（31 個操作詞彙），本地驗證通過 1227 個測試（Codex 229、Security 559、Federation 638）。"
key_points:
  - "Capability Brain 從 61 個已知工具擴展到 353 個自動發現；推薦 p99 0.04 ms、心跳註冊表 p99 0.44 ms"
  - "12 步實現循環標準化開發流程，學習/優化不能自我提升或擴展網絡/密鑰/支出權限"
  - "聯邦 JCS/Ed25519 簽名驗證：1.5 KiB 規範化 p99 8.68 μs、Cognitum action 驗證 p99 81.93 μs（約 13,894 verifications/s）"
tags: [capability-brain, tool-discovery, implementation-loop, federation-security, concurrent-development]
topics: [agents.mcp]
importance: 5
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Ruflo v3.32.29: Capability Brain — Corrected Stable Train

Ruflo v3.32.29 發布，這是 v3.32.28 的修正版（v3.32.28 因發布憑證拒絕未正式發布）。v3.32.29 推進 ruflo/claude-flow/@claude-flow/cli 到 3.32.29，聯邦插件升級到 1.0.0-alpha.18。核心創新是 Ruflo Capability Brain：將原本只知曉 61 個工具的 MCP guidance catalog 升級為可發現全部 353 個工具的實時註冊表，支持按域名過濾、健康檢查、授權驗證。v3.32.29 定義了 12 步實現循環（recall→inspect→route→plan→execute→test→validate→benchmark→optimize→receipt→handoff→authorized publish）和新的聯邦簽名機制（JCS/Ed25519）、Cognitum 產品 API（31 個操作詞彙），本地驗證通過 1227 個測試（Codex 229、Security 559、Federation 638）。

### 重點
- Capability Brain 從 61 個已知工具擴展到 353 個自動發現；推薦 p99 0.04 ms、心跳註冊表 p99 0.44 ms
- 12 步實現循環標準化開發流程，學習/優化不能自我提升或擴展網絡/密鑰/支出權限
- 聯邦 JCS/Ed25519 簽名驗證：1.5 KiB 規範化 p99 8.68 μs、Cognitum action 驗證 p99 81.93 μs（約 13,894 verifications/s）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.29)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Ruflo v3.32.29: Capability Brain — Corrected Stable Train

Ruflo v3.32.29: Capability Brain — Corrected Stable Train 
 v3.32.29 is the corrective stable publication of the Capability Brain work 
first preserved in the immutable 
 v3.32.28 source release . 
The v3.32.28 npm train was not published: its release credential was rejected, 
and the intended federation 1.0.0-alpha.17 coordinate was already occupied by 
an older artifact. Ruflo did not move the existing tag or reuse the immutable 
package coordinate. 
 This release advances ruflo , claude-flow , and @claude-flow/cli to 
 3.32.29 , advances the federation plugin to 1.0.0-alpha.18 , and retains the 
reviewed @claude-flow/security@3.0.0-alpha.14 and 
 @claude-flow/codex@3.0.3 components. The original release and its end-user 
gist remain intact. The corrected end-user guide is available as a 
 separate v3.32.29 gist . 
 Ruflo has grown into a large agentic runtime, but its old MCP guidance catalog 
only knew about 61 of the 353 tools available in a fully equipped process. That 
made powerful features hard to discover and made agents more likely to guess 
at stale tool names. 
 v3.32.29 publishes the Ruflo Capability Brain: a live, machine-readable map of 
the MCP registry, CLI commands, agents, skills, packages, plugins, authority 
boundaries, risk, and the end-to-end implementation loop. Agents can now ask 
Ruflo which capabilities fit a task and automatically choose from tools that 
are actually registered in the current process. 
 What you can use it for 
 
 Discover every MCP tool registered in your running Ruflo server. 
 Route a task to suitable tools, agents, skills, and a swarm topology. 
 Find capabilities across .claude , .agents , installed packages, and Ruflo 
plugins. 
 Keep optional or remote integrations honest: registered, configured, 
reachable, healthy, and authorized are reported as different facts. 
 Guide autonomous development through recall, inspection, planning, 
implementation, testing, validation, benchmarking, optimization, evidence, 
handoff, and authorized publication. 
 Distinguish policy authorization, exclusive work claims, content-safety 
evidence, memory learning, consensus, and release authority. 
 Route Cognitum identity through the implemented PKCE/OOB profile lifecycle, 
while reporting RFC 8628 polling and server-side logout revocation as 
unavailable instead of guessing. 
 
 Try the Capability Brain 
 In Codex, Claude Code, or another MCP client, ask the agent: 
 
 Use Ruflo guidance_brain to recommend the best workflow for implementing 
this task, then follow the returned implementation loop. 
 
 Or call the MCP tool directly: 
 {
 "name" : " guidance_brain " ,
 "arguments" : {
 "mode" : " recommend " ,
 "task" : " Implement a secure API change with concurrent agents, tests, benchmarks, and a release " 
 }
} 
 Useful modes: 
 { "name" : " guidance_brain " , "arguments" :{ "mode" : " overview " }}
{ "name" : " guidance_brain " , "arguments" :{ "mode" : " capabilities " , "domain" : " memory-knowledge " }}
{ "name" : " guidance_brain " , "arguments" :{ "mode" : " coverage " }}
{ "name" : " guidance_brain " , "arguments" :{ "mode" : " ecosystem " }}
{ "name" : " guidance_brain " , "arguments" :{ "mode" : " implementation-loop " }} 
 The existing guidance_capabilities , guidance_recommend , 
 guidance_discover , guidance_workflow , and guidance_quickref tools remain 
compatible. Their old string catalog is now labeled compatibility-only, and 
stale references are never presented as live recommendations. 
 The implementation loop 
 Generated Codex AGENTS.md guidance and capability recommendations now use one 
complete loop: 
 
 Recall relevant memory and ADR constraints. 
 Inspect source, runtime, dependencies, policy, and health. 
 Route to the smallest capable topology and tool set. 
 Plan acceptance criteria, safety, ownership, and validation. 
 Execute in isolated scopes; Ruflo coordinates while the coding agent works. 
 Test focused, regression, and failure paths. 
 Validate types, security, policy, compatibility, and artifacts. 
 Benchmark a source-bound candidate against a source-bound baseline. 
 Optimize measured bottlenecks without weakening safety. 
 Bind claims and evidence to exact source/build inputs. 
 Reconcile concurrent handoffs and disclose limitations. 
 Publish only through a separately authorized release gate. 
 
 Learning and optimization remain proposal/evidence capabilities. They cannot 
promote themselves or expand network, secrets, spending, concurrency, or 
policy authority. 
 Federation and Cognitum foundations 
 This release also adds opt-in foundations for policy-governed federation and 
Cognitum product actions: 
 
 Upgraded federation peers advertise recursive JCS/Ed25519 signatures by 
default. JCS is negotiated only when the join includes a signature-verified 
peer manifest; endpoint-only joins stay untrusted. 
 Legacy federation signatures are restricted to heartbeat and 
 status-broadcast ; consequential legacy messages are rejected on ingress 
and fail closed on egress to legacy-only peers. 
 Inbound federation authorization runs after signature verification and 
before acceptance, replay marking, or event delivery. 
 The Security SDK adds a closed 31-action product vocabulary for the 
Cognitum dashboard, Meta-LLM, Comms, Cog Studio, RuView, and validated 
learning. 
 Product envelopes enforce audience, tenant, freshness, capability, policy, 
Ed25519 signature, action-specific obligations, and atomic replay-store 
hooks. 
 RuView exports are constrained to registered, privacy-minimized semantic 
observations rather than raw sensor payloads. 
 
 Concurrent development foundations 
 The Codex package now exposes: 
 
 content-addressed Git-visible source-state capture; 
 separately declared and recomputable build-input/toolchain evidence; 
 portable path/case ambiguity refusal; 
 in-memory reference implementations for fenced leases, acknowledged inbox 
semantics, and content-addressed run receipts. 
 
 These references are deliberately observe-only, unsigned, non-persistent, and 
single-process. They help adapter authors test semantics; they are not 
distributed release authorities. 
 Install or upgrade 
 npm install --global ruflo@3.32.29
ruflo doctor 
 Or run it without a global install: 
 npx ruflo@3.32.29 --help 
 Package train: 
 
 ruflo@3.32.29 
 claude-flow@3.32.29 
 @claude-flow/cli@3.32.29 
 @claude-flow/codex@3.0.3 
 @claude-flow/security@3.0.0-alpha.14 
 @claude-flow/plugin-agent-federation@1.0.0-alpha.18 
 
 Compatibility 
 
 Existing guidance MCP tools remain available. 
 Existing projects stay in their current policy compatibility mode. 
 JCS federation signing is negotiated; no downgrade occurs after a failed JCS 
verification. 
 Older installations continue local workflows when optional packages are 
absent. 
 The new Codex harness and Cognitum product-plane APIs are additive exports. 
 
 Local validation and benchmarks 
 Validated on Node.js 22/Linux: 
 
 Capability Brain: all 353 observed live tools assigned exactly once; zero 
duplicate or fallback classifications. 
 CLI focused brain/guardrail tests: 12 passing. 
 Codex: 229 tests passing. 
 Security: 559 tests passing. 
 Federation: 638 tests passing. 
 Capability Brain build for a 353-tool registry: p99 about 0.44 ms in the 
latest local run; recommendation p99 about 0.04 ms. 
 1.5 KiB federation JCS canonicalization: p50 8.39 μs, p99 8.68 μs, 
approximately 119,204 operations/second. 
 1.0 KiB signed Cognitum action verification: p50 71.97 μs, p99 81.93 μs, 
approximately 13,894 verifications/second. 
 Source-state capture over a clean 200-file Git fixture averaged 15.77 ms; 
the dirty-patch plus 25-file manifest fixture averaged 27.09 ms. 
 
 These are local microbenchmarks, not cross-platform service SLOs. 
 Important limitations 
 These APIs are an opt-in foundation, not a declaration that distributed claim 
federation is production-ready. Persistent control-plane leases, durable 
inbox/outbox storage, signed receipt ledgers, release-decision composition, 
cross-service identity links, and Cognitum production adapters still require 
deployment-specific implementation and acceptance testing. 
 A lease, signature, claim, score, memory, consensus result, or passing test is 
evidence. None grants product or release authority by itself. 
 Architecture 
 
 ADR-325: zero-trust claim federation and work ownership 
 ADR-326: Cognitum product-plane federation profile 
 ADR-327: federated concurrent development harness 
 ADR-328: Cognitum-assisted agent learning 
 ADR-329: Ruflo Capability Brain for MCP guidance

</details>